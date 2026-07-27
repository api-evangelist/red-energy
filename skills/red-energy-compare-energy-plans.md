---
generated: '2026-07-27'
method: generated
name: Compare Red Energy tariff plans
description: List Red Energy's published electricity and gas plans and pull full tariff detail for the ones worth comparing, with no credential at all.
api: openapi/red-energy-cds-energy-openapi.yml
operations: [listEnergyPlans, getEnergyPlanDetail]
access: anonymous
source: >-
  operationIds verified in openapi/red-energy-cds-energy-openapi.yml; behaviour
  verified live against https://cdr.energymadeeasy.gov.au/red-energy/cds-au/v1 on
  2026-07-27.
---

# Compare Red Energy tariff plans

Red Energy's Consumer Data Right Product Reference Data is fully open. Anyone can read every tariff it sells — 1,705 plans as at 2026-07-27 — with no API key, no signup and no accreditation.

## Auth

None. Do not send an Authorization header; there is nothing to send. See `authentication/red-energy-authentication.yml`.

## Base URL

`https://cdr.energymadeeasy.gov.au/red-energy/cds-au/v1`

Note this is the **Australian Energy Regulator's** Energy Made Easy CDR host under the Red Energy brand path — not a Red Energy domain. In CDR energy, generic plan data is served centrally. Calling `/cds-au/v1/energy/plans` on `public.cdr.redenergy.com.au` returns an nginx 404; that is expected, not an outage.

## The one header that matters

Every Consumer Data Standards endpoint requires an `x-v` request header carrying the endpoint version as a positive integer.

- Omit it and you get `400` `urn:au-cds:error:cds-all:Header/Missing`.
- Ask for a version above the maximum and you get `406` `urn:au-cds:error:cds-all:Header/UnsupportedVersion`, with the maximum reported in `detail`.
- The two operations here are on **different** version trains. `listEnergyPlans` is version 1; `getEnergyPlanDetail` is version 3. Sending `x-v: 1` to plan detail returns `406`.

## Steps

1. **List the plans** — `listEnergyPlans` (`GET /energy/plans`) with `x-v: 1`. Useful query parameters: `fuelType` (`ELECTRICITY`, `GAS`, `DUAL`, `ALL`), `type` (`STANDING`, `MARKET`, `REGULATED`, `ALL`), `effective` (`CURRENT`, `FUTURE`, `ALL`), `updated-since`, plus `page` and `page-size`. Read `meta.totalRecords` and `meta.totalPages` before you start paging; the default `page-size` is 25.
2. **Narrow by geography** — each plan carries a `geography` block with `distributors` and `includedPostcodes` / `excludedPostcodes`. Filter client-side on the customer's postcode; there is no server-side postcode filter.
3. **Pull the detail** — `getEnergyPlanDetail` (`GET /energy/plans/{planId}`) with `x-v: 3` for each shortlisted `planId`. The response adds `electricityContract` (or `gasContract`) with `tariffPeriod`, `fees`, `discounts`, `incentives`, `solarFeedInTariff`, `greenPowerCharges`, `controlledLoad` and `eligibility`.
4. **Compare on the contract, not the display name** — `pricingModel`, `paymentOption`, `isFixed` and the `tariffPeriod` rate blocks are what actually determine cost. Brand marketing names (`displayName`) do not.

## Pagination

Offset, not cursor. `page` defaults to 1, `page-size` defaults to 25. Follow `links.next` until it is absent; `links.last` tells you where you are going. See `conventions/red-energy-conventions.yml`.

## Errors

The envelope is the CDS `errors[]` array — `code` / `title` / `detail` — served as `application/json`. It is **not** RFC 9457 problem+json. Full catalogue in `errors/red-energy-problem-types.yml`. Watch for `422` `Field/InvalidPage` when you page past the end, and note that this implementation omits `detail` on `404 Resource/NotFound`.

## Rate limits

The Consumer Data Standards set a 300 TPS ceiling on all unauthenticated traffic across every consumer of a data holder. Expect `429` if you hammer it, and read `Retry-After`. See `rate-limits/red-energy-rate-limits.yml`.

## Notes

- `planId` values carry an `@EME` suffix (observed `RED552317MRE18@EME`) identifying Energy Made Easy as the serving system.
- Sibling brands under the same Snowy Hydro ownership use the same pattern — `snowy-energy` and `lumo-energy` — but both returned `meta.totalRecords 0` on 2026-07-27. A live register entry does not mean populated data.
- Worked request/response pairs are in `examples/`.
