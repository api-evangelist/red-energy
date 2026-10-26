# Red Energy (red-energy)

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

Red Energy Pty Ltd (ABN 60 107 479 372) is an Australian electricity and gas retailer, wholly owned by Snowy Hydro Ltd, that supplies more than a million residential and business customers across New South Wales, Victoria, Queensland, South Australia and the ACT from a Richmond, Victoria base. It sits on the retail end of the National Electricity Market value chain: Snowy Hydro generates, the distribution network businesses own the poles and wires, AEMO operates the market and holds metering data, and Red Energy owns the customer, the tariff and the bill. Its API posture is entirely a product of statute rather than product strategy. Red Energy publishes no developer portal, no self-serve API programme and no proprietary specification — `developer.`, `api.`, `docs.` and `data.` subdomains do not resolve, and redenergy.com.au itself sits behind a Cloudflare bot challenge that returns HTTP 403 to any non-browser client. What it does have is a real, verified Consumer Data Right implementation: it is a designated CDR energy data holder listed on the CDR Register with the public base URI `https://public.cdr.redenergy.com.au`, which serves the Consumer Data Standards discovery endpoints live with correct `x-v` version negotiation, while 1,705 Red Energy branded plans are published anonymously through the Australian Energy Regulator's Energy Made Easy CDR host.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/red-energy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/red-energy/refs/heads/main/apis.yml)

## Tags

- Energy
- Australia
- Utilities
- Electricity
- Gas
- Energy Retail
- Consumer Data Right
- CDR
- Product Reference Data
- Smart Metering
- Open Data

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## Mandate

| | |
|---|---|
| **Home market** | Australia |
| **Mandate regime** | Consumer Data Right (energy) — Part IVD, Competition and Consumer Act 2010; ACCC as regulator, Treasury Data Standards Body as spec author |
| **Mandate status** | **Live and implemented** — verified via CDR Register entry, a live standards-conformant host on a Red Energy domain, and live branded product reference data |
| **Data standard** | CDR Consumer Data Standards (energy) — CDR Energy API v1.36.0 + CDR Common API v1.36.0, OpenAPI 3.0.3, `x-v` header versioning |
| **Consumer data API** | Yes — accredited CDR data recipients only, with consumer consent |
| **Open market data** | No — Red Energy is a retailer; open NEM/grid data comes from AEMO |
| **Access gate** | Accredited-only for consumer data; no gate at all on product reference data |

Red Energy is the control case for whether an API mandate is replicable. The same statutory machinery that made every Australian bank publish one identical contract was lifted out of banking and applied to energy, and it worked — a retailer with no developer programme of any kind is now a live, register-listed, standards-conformant API publisher. It produced a compliance surface, not a product.

## APIs

### Red Energy CDR Energy Product Reference Data API

The unauthenticated Consumer Data Right Product Reference Data surface for the Red Energy brand — Get Generic Plans and Get Generic Plan Detail from the Consumer Data Standards CDR Energy API. Unlike CDR banking, where each authorised deposit-taking institution serves its own product endpoint, energy plan data is served centrally by the Australian Energy Regulator's Energy Made Easy CDR host under a per-brand path. Confirmed live on 2026-07-27: `GET /cds-au/v1/energy/plans` with header `x-v: 1` returned HTTP 200 with response header `x-v: 1` and `meta.totalRecords` 1705 Red Energy plans; the same call with no `x-v` header returned HTTP 400 and with `x-v: 9` returned HTTP 406. No API key, no signup and no accreditation is needed to call it.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#energy-apis](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- **Base URL:** `https://cdr.energymadeeasy.gov.au/red-energy/cds-au/v1`

#### Tags

- Energy Plans
- Product Reference Data
- Consumer Data Right
- Tariffs
- Australia

#### Properties

- [OpenAPI](openapi/red-energy-cds-energy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-generic-plans)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-generic-plan-detail)
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/)
- [Registry](https://api.cdr.gov.au/cdr-register/v1/energy/data-holders/brands/summary)

### Red Energy CDR Discovery API

Red Energy's own registered Consumer Data Right public base URI, serving the two unauthenticated Data Holder Operations endpoints of the Consumer Data Standards CDR Common API — Get Status and Get Outages. This is the only API surface hosted on a Red Energy controlled domain. Confirmed live on 2026-07-27: `GET /cds-au/v1/discovery/status` with header `x-v: 1` returned HTTP 200 and a CDS-shaped envelope reporting status `OK`; without an `x-v` header it returned HTTP 400, and with `x-v: 3` it returned HTTP 406.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#common-apis](https://consumerdatastandardsaustralia.github.io/standards/#common-apis)
- **Base URL:** `https://public.cdr.redenergy.com.au/cds-au/v1`

#### Tags

- Discovery
- Status
- Outages
- Consumer Data Right
- Australia

#### Properties

- [OpenAPI](openapi/red-energy-cds-common-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-status)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-outages)
- [Status](https://public.cdr.redenergy.com.au/cds-au/v1/discovery/status)
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/)

### Red Energy CDR Energy Consumer Data API

The consumer-authorised half of the Consumer Data Right energy obligation that Red Energy is designated to meet as a data holder — electricity service points, usage, distributed energy resources, energy accounts, balances, invoices, billing, concessions and payment schedules, sixteen paths in all. This surface is real and mandated, but it is not open: it is reachable only by an accredited CDR data recipient, over mutual TLS with FAPI-profile OAuth2 and OpenID Connect, after the individual customer grants consent. No base URL is recorded because none is publicly discoverable, and no endpoint on this surface was called.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#energy-apis](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)

#### Tags

- Energy Accounts
- Electricity Usage
- Billing
- Distributed Energy Resources
- Consumer Data Right
- Australia

#### Properties

- [OpenAPI](openapi/red-energy-cds-energy-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- [Authentication](https://consumerdatastandardsaustralia.github.io/standards/#security-profile)
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/)

## Common Properties

- [Website](https://www.redenergy.com.au/)
- [LinkedIn](https://www.linkedin.com/company/red-energy)
- [Status](https://public.cdr.redenergy.com.au/cds-au/v1/discovery/status)
- [Registry](https://api.cdr.gov.au/cdr-register/v1/energy/data-holders/brands/summary)
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/)

## Maintainers

- **Kin Lane** — kin@apievangelist.com

## Enrichment Artifacts (2026-07-27)

Round 2 of the API Evangelist enrichment pipeline. Nothing below was invented — each artifact is either harvested from a real source, captured live from a production endpoint, or derived from artifacts already in this repository, and every probe records its HTTP status.

| Artifact | What it holds | Method |
|---|---|---|
| [`authentication/`](authentication/red-energy-authentication.yml) | The two-mode auth posture: nothing on the public half, FAPI 1.0 Advanced OAuth2/OIDC over mTLS on the consumer half | searched |
| [`scopes/`](scopes/red-energy-scopes.yml) | 11 CDR authorisation scopes with consumer-facing data-language equivalents | searched |
| [`conventions/`](conventions/red-energy-conventions.yml) | `x-v` version negotiation, offset pagination, `x-fapi-interaction-id` tracing, CDS error envelope — and the absence of any idempotency contract | searched |
| [`errors/`](errors/red-energy-problem-types.yml) | The `urn:au-cds:error:...` registry; three codes observed live | searched |
| [`lifecycle/`](lifecycle/red-energy-lifecycle.yml) | Per-endpoint versioning, Endpoint Version Schedule as deprecation policy, 99.5% availability obligation, latency tiers | searched |
| [`rate-limits/`](rate-limits/red-energy-rate-limits.yml) | CDS traffic thresholds and the 10-calls-per-24-hours velocity limits on NMI, usage and DER data | searched |
| [`conformance/`](conformance/red-energy-conformance.yml) | Standards conformance separated into behaviourally verified versus statutorily asserted | searched |
| [`changelog/`](changelog/red-energy-changelog.yml) | The DSB standards changelog that governs this contract | searched |
| [`examples/`](examples/) | Seven request/response pairs captured live, including the 400, 404 and 406 error shapes | searched |
| [`data-model/`](data-model/red-energy-data-model.yml) | The entity graph derived from 160 component schemas | derived |
| [`overlays/`](overlays/) | OpenAPI Overlay 1.0.0 recording the real hosts and the anonymous/accredited split, without mutating the DSB documents | generated |
| [`agentic-access/`](agentic-access/red-energy-agentic-access.yml) | All 27 operations classified `connected`/`read` — nothing on this API mutates anything | generated |
| [`skills/`](skills/_index.yml) | Three packaged agent skills grounded in verified operationIds | generated |
| [`arazzo/`](arazzo/red-energy-compare-plans-workflow.yml) | A runnable four-step workflow across both public hosts | generated |
| [`mcp/`](mcp/red-energy-mcp.yml) | Candidate MCP tool set plus a tool-to-operation crosswalk. No MCP server exists in the CDR ecosystem | derived |
| [`llms/`](llms/red-energy-llms.txt) | Generated llms.txt. No `/llms.txt` is published on any host | generated |
| [`packages/`](packages/red-energy-packages.yml) | Registry search results — no first-party SDK anywhere — plus the DSB/ACCC ecosystem tooling | searched |
| [`security/`](security/red-energy-domain-security.yml) | TLS, HSTS, DNSSEC, CAA, SPF and DMARC probe results | probed |
| [`well-known/`](well-known/red-energy-well-known.yml) | Every `/.well-known/` and spec-discovery probe and its status. All missed — recorded as a negative, not omitted | searched |

### Recorded negatives

No webhooks or event surface, so no AsyncAPI. No CLI, no embedded UI components, no sandbox published by Red Energy, no first-party SDK, no Postman collection, no gRPC, no GraphQL, no vulnerability disclosure programme and no trust centre. `www.redenergy.com.au` returns HTTP 403 with a Cloudflare bot challenge to every programmatic client, including its own CDR policy PDF.
