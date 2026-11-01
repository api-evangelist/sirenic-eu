# Sirenic

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

Sirenic is a French pay-per-call API for official company data across France and Europe, built for AI agents. It serves company search and profiles by SIREN/SIRET from INSEE Sirene and INPI RNE, establishments, officers, filed accounts and ratios, BODACC legal alerts, a default-risk score, sanctions screening against six official lists, KYB dossiers, live VIES VAT and IBAN checks with a ready-to-invoice verdict for the 2026 French e-invoicing mandate, public-procurement records, watchlists with Ed25519-signed webhooks, and profiles, accounts and events from thirteen European registers plus LEI/GLEIF groups. Every /v1 route is a GET priced per call ($0.002 to $1.00) and paid either through the x402 protocol in USDC or EURC on Base with no account, or with an srn_live_ API key and prepaid euro credits. It publishes an OpenAPI 3.1, llms.txt, an RFC 9727 api-catalog, an MCP server, an A2A agent card, x402 discovery and OAuth metadata from api.sirenic.eu.

**Areas:** Company Data · Business Registry · KYB · Sanctions Screening · Financial Data · Credit Risk · VAT Validation · IBAN Validation · E-Invoicing · Public Procurement · Open Data · France

## Sirenic on APIs.io

Everything profiled for Sirenic is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/sirenic-eu/](https://apis.io/providers/sirenic-eu/)** — or go straight to one of the APIs or properties below.

### APIs (33)

- [Sirenic MCP Server](https://apis.io/apis/sirenic-eu/sirenic-mcp-server/) — Remote Model Context Protocol server (streamable HTTP) over the same official French and European company-data routes: 77 tools such as…
- [Sirenic A2A Agent](https://apis.io/apis/sirenic-eu/sirenic-a2a-agent/) — Agent2Agent JSON-RPC endpoint exposing the 116 paid routes as A2A skills (skill ids are the OpenAPI path templates) with the a2a-x402 v0.1 payment…
- [Sirenic Acheteur API](https://apis.io/apis/sirenic-eu/sirenic-eu-acheteur-api/) — The Acheteur API from Sirenic — 1 operation(s) for acheteur.
- [Sirenic Association API](https://apis.io/apis/sirenic-eu/sirenic-eu-association-api/) — The Association API from Sirenic — 2 operation(s) for association.
- [Sirenic Associations API](https://apis.io/apis/sirenic-eu/sirenic-eu-associations-api/) — The Associations API from Sirenic — 1 operation(s) for associations.
- [Sirenic Bodacc API](https://apis.io/apis/sirenic-eu/sirenic-eu-bodacc-api/) — The Bodacc API from Sirenic — 1 operation(s) for bodacc.
- [Sirenic Comparer API](https://apis.io/apis/sirenic-eu/sirenic-eu-comparer-api/) — The Comparer API from Sirenic — 1 operation(s) for comparer.
- [Sirenic Demo API](https://apis.io/apis/sirenic-eu/sirenic-eu-demo-api/) — The Demo API from Sirenic — 1 operation(s) for demo.
- [Sirenic Dirigeant API](https://apis.io/apis/sirenic-eu/sirenic-eu-dirigeant-api/) — The Dirigeant API from Sirenic — 1 operation(s) for dirigeant.
- [Sirenic Documents API](https://apis.io/apis/sirenic-eu/sirenic-eu-documents-api/) — The Documents API from Sirenic — 1 operation(s) for documents.
- [Sirenic Entreprise API](https://apis.io/apis/sirenic-eu/sirenic-eu-entreprise-api/) — The Entreprise API from Sirenic — 21 operation(s) for entreprise.
- [Sirenic Eu API](https://apis.io/apis/sirenic-eu/sirenic-eu-eu-api/) — The Eu API from Sirenic — 70 operation(s) for eu.
- [Sirenic Facturation API](https://apis.io/apis/sirenic-eu/sirenic-eu-facturation-api/) — The Facturation API from Sirenic — 1 operation(s) for facturation.
- [Sirenic Facture API](https://apis.io/apis/sirenic-eu/sirenic-eu-facture-api/) — The Facture API from Sirenic — 1 operation(s) for facture.
- [Sirenic Healthz API](https://apis.io/apis/sirenic-eu/sirenic-eu-healthz-api/) — The Healthz API from Sirenic — 1 operation(s) for healthz.
- [Sirenic Iban API](https://apis.io/apis/sirenic-eu/sirenic-eu-iban-api/) — The Iban API from Sirenic — 1 operation(s) for iban.
- [Sirenic Intelligence API](https://apis.io/apis/sirenic-eu/sirenic-eu-intelligence-api/) — The Intelligence API from Sirenic — 1 operation(s) for intelligence.
- [Sirenic Kyb API](https://apis.io/apis/sirenic-eu/sirenic-eu-kyb-api/) — The Kyb API from Sirenic — 2 operation(s) for kyb.
- [Sirenic Lecture API](https://apis.io/apis/sirenic-eu/sirenic-eu-lecture-api/) — The Lecture API from Sirenic — 1 operation(s) for lecture.
- [Sirenic Marches API](https://apis.io/apis/sirenic-eu/sirenic-eu-marches-api/) — The Marches API from Sirenic — 1 operation(s) for marches.
- [Sirenic Preview API](https://apis.io/apis/sirenic-eu/sirenic-eu-preview-api/) — The Preview API from Sirenic — 1 operation(s) for preview.
- [Sirenic Prospection API](https://apis.io/apis/sirenic-eu/sirenic-eu-prospection-api/) — The Prospection API from Sirenic — 1 operation(s) for prospection.
- [Sirenic Provenance API](https://apis.io/apis/sirenic-eu/sirenic-eu-provenance-api/) — The Provenance API from Sirenic — 1 operation(s) for provenance.
- [Sirenic Rapport API](https://apis.io/apis/sirenic-eu/sirenic-eu-rapport-api/) — The Rapport API from Sirenic — 1 operation(s) for rapport.
- [Sirenic Recherche API](https://apis.io/apis/sirenic-eu/sirenic-eu-recherche-api/) — The Recherche API from Sirenic — 1 operation(s) for recherche.
- [Sirenic Regulateurs API](https://apis.io/apis/sirenic-eu/sirenic-eu-regulateurs-api/) — The Regulateurs API from Sirenic — 1 operation(s) for regulateurs.
- [Sirenic Reperer API](https://apis.io/apis/sirenic-eu/sirenic-eu-reperer-api/) — The Reperer API from Sirenic — 1 operation(s) for reperer.
- [Sirenic Sanctions API](https://apis.io/apis/sirenic-eu/sirenic-eu-sanctions-api/) — The Sanctions API from Sirenic — 1 operation(s) for sanctions.
- [Sirenic Score API](https://apis.io/apis/sirenic-eu/sirenic-eu-score-api/) — The Score API from Sirenic — 1 operation(s) for score.
- [Sirenic Secteur API](https://apis.io/apis/sirenic-eu/sirenic-eu-secteur-api/) — The Secteur API from Sirenic — 1 operation(s) for secteur.
- [Sirenic Suggestions API](https://apis.io/apis/sirenic-eu/sirenic-eu-suggestions-api/) — The Suggestions API from Sirenic — 1 operation(s) for suggestions.
- [Sirenic Surveillance API](https://apis.io/apis/sirenic-eu/sirenic-eu-surveillance-api/) — The Surveillance API from Sirenic — 4 operation(s) for surveillance.
- [Sirenic Tva API](https://apis.io/apis/sirenic-eu/sirenic-eu-tva-api/) — The Tva API from Sirenic — 1 operation(s) for tva.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Sirenic Eu Webhooks](https://apis.io/asyncapis/sirenic-eu/sirenic-eu-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [sirenic](https://apis.io/servers/sirenic-eu/sirenic/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Sirenic Eu Agentic Access](https://apis.io/agentic-access/sirenic-eu/sirenic-eu-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Sirenic Eu Openapi Overlay](https://apis.io/overlays/sirenic-eu/sirenic-eu-openapi-overlay/)

#### Security (1)

Authentication, trust centre, and vulnerability disclosure.

- [Sirenic Eu Authentication](https://apis.io/security/sirenic-eu/sirenic-eu-authentication/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Sirenic Eu Scopes](https://apis.io/scopes/sirenic-eu/sirenic-eu-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Sirenic Eu Plans Pricing](https://apis.io/plans/sirenic-eu/sirenic-eu-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Sirenic Eu Rate Limits](https://apis.io/rate-limits/sirenic-eu/sirenic-eu-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://sirenic.eu/)
- [Documentation](https://api.sirenic.eu/api)
- [Getting started](https://github.com/sirenic-eu/sirenic-examples)
- [API reference](https://api.sirenic.eu/api)
- [Blog](https://api.sirenic.eu/articles)
- [Privacy policy](https://api.sirenic.eu/confidentialite)
- [GitHub](https://github.com/sirenic-eu)

## API Evangelist rating

**Kin Score 58.5** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 58.2 |
| Contract governance | 18.2 |
| Operational transparency | 44.7 |
| Developer ergonomics | 73.2 |
| Access clarity | 50.0 |

**Agent readiness 71.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | yes |
| Agent Card | conformant |
| Dry Run Mode | na |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 41.2** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/sirenic-eu/](https://apis.io/providers/sirenic-eu/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Sirenic: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/sirenic-eu/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
