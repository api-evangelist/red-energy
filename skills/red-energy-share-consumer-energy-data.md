---
generated: '2026-07-27'
method: generated
name: Retrieve a consenting customer's energy data as an accredited data recipient
description: The end-to-end shape of a CDR energy data-sharing call against Red Energy — what accreditation and consent you need first, then the account, billing, service point and usage operations in the order they depend on each other.
api: openapi/red-energy-cds-energy-openapi.yml
operations: [listEnergyAccounts, getEnergyAccountDetail, getEnergyAccountBalance, getBillingForEnergyAccount, listElectricityServicePoints, getElectricityServicePointUsage]
access: accredited-only
source: >-
  operationIds verified in openapi/red-energy-cds-energy-openapi.yml and
  openapi/red-energy-cds-common-openapi.yml. Behaviour is NOT verified — this
  surface cannot be reached without ACCC accreditation, CDR CA certificates and a
  consented authorisation, and no endpoint on it was called. Grounded in the
  Consumer Data Standards, not in an observed response.
---

# Retrieve a consenting customer's energy data as an accredited data recipient

This skill describes a surface that is real and mandated but **gated by statute, not by a signup form**. An agent cannot run it opportunistically. Read the prerequisites before writing any code.

## Prerequisites — none of these are optional

1. **Accreditation.** Become an accredited person under the CDR rules via the ACCC — unrestricted or sponsored accreditation, or operate as a CDR representative or under the trusted adviser pathway.
2. **Certificates.** Obtain CDR Register client credentials plus transport and signing certificates from the CDR Certificate Authority. Both ends of the mutual-TLS handshake must present CDR CA-issued certificates; certificates from any other authority MUST be rejected.
3. **Conformance testing.** Pass the ACCC Conformance Test Suite before activation on the Register.
4. **Consent.** Initiate an authorisation the individual Red Energy customer approves. Consent is explicit, scoped and time-limited, and the customer can amend or withdraw it at any time from a CDR-mandated consumer dashboard.

There is no self-serve path, no sandbox published by Red Energy, and no commercial API deal. The gate is statutory.

## Auth

OAuth 2.0 authorization code flow with PKCE `S256`, under the FAPI 1.0 Advanced profile, over mutual TLS: pushed authorisation requests, a signed request object (`ES256` or `PS256`), `private_key_jwt` client authentication, and access tokens sender-constrained to your client certificate. Full profile in `authentication/red-energy-authentication.yml`.

**Red Energy's authorisation endpoints are not publicly discoverable.** `GET https://public.cdr.redenergy.com.au/.well-known/openid-configuration` returned `404` on 2026-07-27. The infosec base URI is published only through the authenticated portion of the CDR Register — resolve it there, do not guess a host.

## Scopes

Request only what you need; the consumer sees the data-language equivalent of every scope on the consent screen.

| Scope | Gets you |
|---|---|
| `energy:accounts.basic:read` | `listEnergyAccounts` |
| `energy:accounts.detail:read` | `getEnergyAccountDetail` |
| `energy:billing:read` | balances, billing, invoices |
| `energy:electricity.servicepoints.basic:read` | `listElectricityServicePoints` |
| `energy:electricity.servicepoints.detail:read` | `getElectricityServicePointDetail` |
| `energy:electricity.usage:read` | usage reads |
| `energy:electricity.der:read` | distributed energy resources |

Detail scopes are additive — granting one without its basic counterpart is meaningless. Full reference in `scopes/red-energy-scopes.yml`.

## Steps

1. **List accounts** — `listEnergyAccounts` (`GET /energy/accounts`, `x-v: 2`). Capture each `accountId`. Everything downstream keys off it.
2. **Get account detail** — `getEnergyAccountDetail` (`GET /energy/accounts/{accountId}`, `x-v: 4`) for the plan, tariff and additional-users view. Also yields the `servicePointIds` attached to the account.
3. **Get the balance** — `getEnergyAccountBalance` (`GET /energy/accounts/{accountId}/balance`, `x-v: 1`). For many accounts at once use `listEnergyAccountBalancesBulk` or POST the id set to `listEnergyAccountBalancesSpecificAccounts`.
4. **Get billing history** — `getBillingForEnergyAccount` (`GET /energy/accounts/{accountId}/billing`, `x-v: 3`), bounded with `oldest-time` / `newest-time`. Defaults to the last 12 months when omitted.
5. **List service points** — `listElectricityServicePoints` (`GET /energy/electricity/servicepoints`, `x-v: 2`). The `servicePointId` is a **tokenised** NMI, not the raw NMI.
6. **Get usage** — `getElectricityServicePointUsage` (`GET /energy/electricity/servicepoints/{servicePointId}/usage`, `x-v: 1`), or the bulk / POST-as-query variants for many service points.

## Header discipline

Every call needs `x-v`. Authenticated calls also carry `x-fapi-auth-date`; customer-present calls add `x-fapi-customer-ip-address` and `x-cds-client-headers` (Base64). The presence of `x-fapi-customer-ip-address` is what marks a call customer-present, which changes both your rate limits and your latency SLA. Always send `x-fapi-interaction-id` as an RFC 4122 UUID and log the one played back.

## Idempotency

There is none, and none is needed. This surface is read-only — 22 of 27 operations are `GET`, and the five `POST` operations are POST-as-query (they carry a long id list in the body and create nothing). Do not look for an `Idempotency-Key` header; the standard has no such thing.

## Rate limits that will actually bite you

Unattended traffic is capped hard: 20 sessions per day per customer per software product, 100 calls per session, 5 TPS per session. On top of that, three energy data sets carry a **velocity limit of 10 calls per 24 hours**: NMI standing data (`getElectricityServicePointDetail`), usage, and DER. Cache accordingly. See `rate-limits/red-energy-rate-limits.yml`.

## Errors

The CDS `errors[]` envelope. The ones specific to this flow:

- `403 urn:au-cds:error:cds-all:Authorisation/RevokedConsent` — the customer withdrew consent. Stop; do not retry.
- `403 .../Authorisation/InvalidConsent` — your consent does not cover the resource or the requested scope.
- `403 .../Authorisation/AdrStatusNotActive` — your software product is not active on the Register.
- `404 urn:au-cds:error:cds-energy:Authorisation/InvalidEnergyAccount` — permanently unavailable; stop asking.
- `404 .../UnavailableEnergyAccount` / `.../UnavailableServicePoint` — temporary; a later request may succeed.

Full catalogue in `errors/red-energy-problem-types.yml`.

## Secondary data holder

Interval metering and NMI standing data originate with **AEMO** as the CDR secondary data holder; Red Energy makes a Shared Responsibility Data Request for them. Errors propagated from AEMO carry `isSecondaryDataHolderError: true`, and AEMO being down does not mean Red Energy is down. Handle that distinction rather than treating every failure as the retailer's.
