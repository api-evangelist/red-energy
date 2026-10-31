# Red Energy

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Red Energy Pty Ltd (ABN 60 107 479 372) is an Australian electricity and gas retailer, wholly owned by Snowy Hydro Ltd, that supplies more than a million residential and business customers across New South Wales, Victoria, Queensland, South Australia and the ACT from a Richmond, Victoria base. It sits on the retail end of the National Electricity Market value chain: Snowy Hydro generates, the distribution network businesses own the poles and wires, AEMO operates the market and holds metering data, and Red Energy owns the customer, the tariff and the bill. Its API posture is entirely a product of statute rather than product strategy. Red Energy publishes no developer portal, no self-serve API programme and no proprietary specification - developer., api., docs. and data. subdomains do not resolve, and redenergy.com.au itself sits behind a Cloudflare bot challenge that returns HTTP 403 to any non-browser client. What it does have is a real, verified Consumer Data Right implementation: it is a designated CDR energy data holder listed on the CDR Register with the public base URI https://public.cdr.redenergy.com.au, which serves the Consumer Data Standards discovery endpoints live with correct x-v version negotiation, while 1,705 Red Energy branded plans are published anonymously through the Australian Energy Regulator's Energy Made Easy CDR host. The split is the story - open, standardised, anonymous product reference data on one side, and consumer usage, billing and account data available only to accredited CDR data recipients with the customer's consent on the other, with nothing at all in between.

**Areas:** Energy · Australia · Utilities · Electricity · Gas · Energy Retail · Consumer Data Right · CDR · Product Reference Data · Smart Metering · Open Data

## Red Energy on APIs.io

Everything profiled for Red Energy is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/red-energy/](https://apis.io/providers/red-energy/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [Red Energy Data Holder Customers API](https://apis.io/apis/red-energy/red-energy-data-holder-customers-api/) — Data Holder Customer endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a CDR…
- [Red Energy Data Holder Operations API](https://apis.io/apis/red-energy/red-energy-data-holder-operations-api/) — Data Holder Operations endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a…
- [Red Energy Distributed Energy Resources API](https://apis.io/apis/red-energy/red-energy-distributed-energy-resources-api/) — Distributed Energy Resource endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as…
- [Red Energy Electricity Service Points API](https://apis.io/apis/red-energy/red-energy-electricity-service-points-api/) — Electricity Service Point endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a…
- [Red Energy Electricity Usage API](https://apis.io/apis/red-energy/red-energy-electricity-usage-api/) — Electricity Usage endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a CDR…
- [Red Energy Account Balances API](https://apis.io/apis/red-energy/red-energy-energy-account-balances-api/) — Energy Account Balance endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a…
- [Red Energy Account Billing API](https://apis.io/apis/red-energy/red-energy-energy-account-billing-api/) — Energy Account Billing endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a…
- [Red Energy Accounts API](https://apis.io/apis/red-energy/red-energy-energy-accounts-api/) — Energy Account endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a CDR energy…
- [Red Energy Plans API](https://apis.io/apis/red-energy/red-energy-energy-plans-api/) — Energy Plan endpoints. Contract is the Consumer Data Standards (Data Standards Body, dsb.gov.au) specification that Red Energy implements as a CDR energy…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (1)

Multi-step workflows that chain operations into a business task.

- [Compare Red Energy tariff plans](https://apis.io/arazzos/red-energy/red-energy-compare-plans-workflow/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [red-energy-cdr](https://apis.io/servers/red-energy/red-energy-cdr/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Red Energy Agentic Access](https://apis.io/agentic-access/red-energy/red-energy-agentic-access/)

#### JSON Schema (19)

The data models the API reads and writes.

- [EnergyAccountDetailResponseV4](https://apis.io/schemas/red-energy/red-energy-energy-account-detail-response-v4/)
- [EnergyAccountListResponseV2](https://apis.io/schemas/red-energy/red-energy-energy-account-list-response-v2/)
- [EnergyBalanceListResponse](https://apis.io/schemas/red-energy/red-energy-energy-balance-list-response/)
- [EnergyBalanceResponse](https://apis.io/schemas/red-energy/red-energy-energy-balance-response/)
- [EnergyBillingListResponseV3](https://apis.io/schemas/red-energy/red-energy-energy-billing-list-response-v3/)
- [EnergyConcessionsResponse](https://apis.io/schemas/red-energy/red-energy-energy-concessions-response/)
- [EnergyDerDetailResponse](https://apis.io/schemas/red-energy/red-energy-energy-der-detail-response/)
- [EnergyDerListResponse](https://apis.io/schemas/red-energy/red-energy-energy-der-list-response/)
- [EnergyInvoiceListResponse](https://apis.io/schemas/red-energy/red-energy-energy-invoice-list-response/)
- [EnergyPaymentScheduleResponse](https://apis.io/schemas/red-energy/red-energy-energy-payment-schedule-response/)
- [EnergyPlanListResponse](https://apis.io/schemas/red-energy/red-energy-energy-plan-list-response/)
- [EnergyPlanResponseV3](https://apis.io/schemas/red-energy/red-energy-energy-plan-response-v3/)
- [EnergyServicePointDetailResponseV2](https://apis.io/schemas/red-energy/red-energy-energy-service-point-detail-response-v2/)
- [EnergyServicePointListResponseV2](https://apis.io/schemas/red-energy/red-energy-energy-service-point-list-response-v2/)
- [EnergyUsageListResponse](https://apis.io/schemas/red-energy/red-energy-energy-usage-list-response/)
- [ResponseCommonCustomer](https://apis.io/schemas/red-energy/red-energy-response-common-customer/)
- [ResponseCommonCustomerDetailV2](https://apis.io/schemas/red-energy/red-energy-response-common-customer-detail-v2/)
- [ResponseCommonDiscoveryStatus](https://apis.io/schemas/red-energy/red-energy-response-common-discovery-status/)
- [ResponseDiscoveryOutagesList](https://apis.io/schemas/red-energy/red-energy-response-discovery-outages-list/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Red Energy Context](https://apis.io/jsonld/red-energy/red-energy-context/)

#### Examples (7)

Example requests and responses.

- [Red Energy Error Missing X V Example](https://apis.io/examples/red-energy/red-energy-error-missing-x-v-example/)
- [Red Energy Error Plan Not Found Example](https://apis.io/examples/red-energy/red-energy-error-plan-not-found-example/)
- [Red Energy Error Unsupported Version Example](https://apis.io/examples/red-energy/red-energy-error-unsupported-version-example/)
- [Red Energy Get Energy Plan Detail Example](https://apis.io/examples/red-energy/red-energy-get-energy-plan-detail-example/)
- [Red Energy Get Outages Example](https://apis.io/examples/red-energy/red-energy-get-outages-example/)
- [Red Energy Get Status Example](https://apis.io/examples/red-energy/red-energy-get-status-example/)
- [Red Energy List Energy Plans Example](https://apis.io/examples/red-energy/red-energy-list-energy-plans-example/)

#### Collections (2)

Postman and Open Collection request collections.

- [CDR Common API](https://apis.io/collections/red-energy/open-red-energy-cds-common/)
- [CDR Energy API](https://apis.io/collections/red-energy/open-red-energy-cds-energy/)

#### Overlays (9)

OpenAPI overlays, including conversational phrasing for each operation.

- [Red Energy Data Holder Customers Api Overlay](https://apis.io/overlays/red-energy/red-energy-data-holder-customers-api-overlay/)
- [Red Energy Data Holder Operations Api Overlay](https://apis.io/overlays/red-energy/red-energy-data-holder-operations-api-overlay/)
- [Red Energy Distributed Energy Resources Api Overlay](https://apis.io/overlays/red-energy/red-energy-distributed-energy-resources-api-overlay/)
- [Red Energy Electricity Service Points Api Overlay](https://apis.io/overlays/red-energy/red-energy-electricity-service-points-api-overlay/)
- [Red Energy Electricity Usage Api Overlay](https://apis.io/overlays/red-energy/red-energy-electricity-usage-api-overlay/)
- [Red Energy Energy Account Balances Api Overlay](https://apis.io/overlays/red-energy/red-energy-energy-account-balances-api-overlay/)
- [Red Energy Energy Account Billing Api Overlay](https://apis.io/overlays/red-energy/red-energy-energy-account-billing-api-overlay/)
- [Red Energy Energy Accounts Api Overlay](https://apis.io/overlays/red-energy/red-energy-energy-accounts-api-overlay/)
- [Red Energy Energy Plans Api Overlay](https://apis.io/overlays/red-energy/red-energy-energy-plans-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Red Energy API Rules](https://apis.io/rules/red-energy/red-energy-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Red Energy Authentication](https://apis.io/security/red-energy/red-energy-authentication/)
- [Red Energy Domain Security](https://apis.io/security/red-energy/red-energy-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Red Energy Scopes](https://apis.io/scopes/red-energy/red-energy-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Red Energy Plans Pricing](https://apis.io/plans/red-energy/red-energy-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Red Energy Rate Limits](https://apis.io/rate-limits/red-energy/red-energy-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.redenergy.com.au/)
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/)
- [API reference](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- [Pricing](https://www.redenergy.com.au/products/)
- [Sign up](https://myaccount.redenergy.com.au/registration)
- [Support](https://www.redenergy.com.au/contactus/)
- [Compliance](https://www.redenergy.com.au/docs/Red-Energy-Consumer-Data-Right-Policy.pdf)
- [Terms of service](https://www.redenergy.com.au/terms-and-conditions/)
- [Privacy policy](https://www.redenergy.com.au/privacy-policy/index.html)
- [Status](https://public.cdr.redenergy.com.au/cds-au/v1/discovery/status)

## API Evangelist rating

**Kin Score 55.0** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 62.9 |
| Contract governance | 33.3 |
| Operational transparency | 68.4 |
| Developer ergonomics | 35.1 |
| Access clarity | 52.6 |

**Agent readiness 29.2** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 38.5** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/red-energy/](https://apis.io/providers/red-energy/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Red Energy: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/red-energy/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
