---
generated: '2026-07-27'
method: generated
name: Check Red Energy CDR availability before calling
description: Read Red Energy's mandated CDR health and scheduled-outage endpoints so an agent can decide whether to proceed, back off, or wait out a planned outage.
api: openapi/red-energy-cds-common-openapi.yml
operations: [getStatus, getOutages]
access: anonymous
source: >-
  operationIds verified in openapi/red-energy-cds-common-openapi.yml; behaviour
  verified live against https://public.cdr.redenergy.com.au/cds-au/v1 on
  2026-07-27.
---

# Check Red Energy CDR availability before calling

Every designated CDR data holder must serve two unauthenticated Data Holder Operations endpoints from its registered public base URI. For Red Energy this is the only API surface on a Red-Energy-controlled domain, and it is the machine-readable substitute for a status page — there is no HTML status page and no developer portal.

## Auth

None. Both endpoints are unauthenticated by design; the Consumer Data Standards forbid mutual TLS on them.

## Base URL

`https://public.cdr.redenergy.com.au/cds-au/v1`

This URI is not guessed — it is the `publicBaseUri` published for `dataHolderBrandId 39230258-a56c-ee11-a81c-002248e31327` in the CDR Register's Get Data Holder Brands Summary endpoint.

## Steps

1. **Read the health status** — `getStatus` (`GET /discovery/status`) with `x-v: 1`. The response is `{"data": {"status", "updateTime", "explanation"}, "links": {"self"}, "meta": {}}`. `status` is one of `OK`, `PARTIAL_FAILURE`, `UNAVAILABLE` or `SCHEDULED_OUTAGE`. Observed on 2026-07-27: `OK`, "All services operational".
2. **Branch on the status** — proceed on `OK`; degrade gracefully on `PARTIAL_FAILURE`; do not retry aggressively on `UNAVAILABLE` or `SCHEDULED_OUTAGE`.
3. **Read the outage schedule** — `getOutages` (`GET /discovery/outages`) with `x-v: 1`. Returns `data.outages[]`, each with `outageTime`, `duration`, `isPartial` and `explanation`. An empty array (observed 2026-07-27) means no planned outage is currently published.
4. **Plan unattended work around it** — the standards require normal planned outages to be published to data recipients with at least one week of lead time, so this endpoint is a real scheduling input, not decoration. Unnotified outages are permitted only to fix a critical service or security issue.

## Version negotiation

Both endpoints are version 1. `x-v: 1` returns `200` with `x-v: 1` echoed. No `x-v` returns `400` `Header/Missing`; `x-v: 3` returns `406` `Header/UnsupportedVersion`. Use `x-min-v` if you want to accept a range.

## What you can conclude, and what you cannot

A `200 OK` here says Red Energy's CDR implementation is up. It does **not** tell you anything about the Product Reference Data surface, which lives on the Australian Energy Regulator's host (`cdr.energymadeeasy.gov.au`) and has no equivalent status endpoint. Check both independently.

## Service levels

The Consumer Data Standards bind Red Energy to 99.5% availability per month excluding planned outages, and to answering 95% of calls per hour within a per-tier threshold — 1000ms for `getStatus` and `getOutages`, which sit in the High Priority tier. See `lifecycle/red-energy-lifecycle.yml`.

## Notes

- The response carries `strict-transport-security: max-age=63072000; includeSubDomains`, `x-content-type-options: nosniff` and `x-frame-options: DENY`.
- `access-control-allow-origin: *` — this endpoint is callable directly from a browser.
- Worked responses are in `examples/red-energy-get-status-example.json` and `examples/red-energy-get-outages-example.json`.
