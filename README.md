# Red Energy (red-energy)

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
