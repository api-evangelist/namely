# Namely

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

Namely is a mid-market Human Capital Management (HCM) platform combining HR, payroll, onboarding, benefits administration, time and attendance, performance management and applicant tracking, delivered as a multi-tenant SaaS on customer subdomains. It publishes a public developer portal on Stoplight carrying a Swagger 2.0 contract for its REST API v1 (39 paths, 54 operations, 95 schemas) covering employee profiles, the tenant-specific profile field schema, groups and teams, job titles and tiers, company resources, the social home feed, notifications and reports. Alongside the REST API, Namely runs a SCIM 2.0 provisioning surface acting as the source of record for identity providers such as Okta, and supports SAML 2.0 single sign-on as a service provider. Authentication is either a 3-legged OAuth 2.0 authorization code grant for partner integrations or a Personal Access Token for a customer's own integrations, both minted inside the customer's own tenant. Namely merged into the combined Vensure Employer Solutions / PrismHR organisation in September 2022.

**Areas:** Human Resources · HCM · Payroll · Employee Data · Onboarding · Benefits · Applicant Tracking · Performance Management · SCIM · SSO · Identity Provisioning · Workforce Management

## Namely on APIs.io

Everything profiled for Namely is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/namely/](https://apis.io/providers/namely/)** — or go straight to one of the APIs or properties below.

### APIs (19)

- [Namely Comments API](https://apis.io/apis/namely/namely-comments-api/) — The Comments API from Namely — 3 operation(s) for comments.
- [Namely Company Info API](https://apis.io/apis/namely/namely-company-info-api/) — The Company Info API from Namely — 1 operation(s) for company info.
- [Namely Company Resources API](https://apis.io/apis/namely/namely-company-resources-api/) — The Company Resources API from Namely — 5 operation(s) for company resources.
- [Namely Countries API](https://apis.io/apis/namely/namely-countries-api/) — The Countries API from Namely — 2 operation(s) for countries.
- [Namely Events API](https://apis.io/apis/namely/namely-events-api/) — The Events API from Namely — 2 operation(s) for events.
- [Namely Groups API](https://apis.io/apis/namely/namely-groups-api/) — The Groups API from Namely — 3 operation(s) for groups.
- [Namely Groups & Teams API](https://apis.io/apis/namely/namely-groups-teams-api/) — The Groups & Teams API from Namely — 7 operation(s) for groups & teams.
- [Namely Home Feed API](https://apis.io/apis/namely/namely-home-feed-api/) — The Home Feed API from Namely — 10 operation(s) for home feed.
- [Namely Job Tier API](https://apis.io/apis/namely/namely-job-tier-api/) — The Job Tier API from Namely — 2 operation(s) for job tier.
- [Namely Job Title API](https://apis.io/apis/namely/namely-job-title-api/) — The Job Title API from Namely — 2 operation(s) for job title.
- [Namely Jobs Info API](https://apis.io/apis/namely/namely-jobs-info-api/) — The Jobs Info API from Namely — 4 operation(s) for jobs info.
- [Namely Likes API](https://apis.io/apis/namely/namely-likes-api/) — The Likes API from Namely — 1 operation(s) for likes.
- [Namely System Info API](https://apis.io/apis/namely/namely-namely-system-info-api/) — The Namely System Info API from Namely — 2 operation(s) for namely system info.
- [Namely Notifications API](https://apis.io/apis/namely/namely-notifications-api/) — The Notifications API from Namely — 2 operation(s) for notifications.
- [Namely Profile Fields API](https://apis.io/apis/namely/namely-profile-fields-api/) — The Profile Fields API from Namely — 4 operation(s) for profile fields.
- [Namely Profile Fields Sections API](https://apis.io/apis/namely/namely-profile-fields-sections-api/) — The Profile Fields Sections API from Namely — 2 operation(s) for profile fields sections.
- [Namely Profiles API](https://apis.io/apis/namely/namely-profiles-api/) — The Profiles API from Namely — 3 operation(s) for profiles.
- [Namely Reports API](https://apis.io/apis/namely/namely-reports-api/) — The Reports API from Namely — 1 operation(s) for reports.
- [Namely Teams API](https://apis.io/apis/namely/namely-teams-api/) — The Teams API from Namely — 1 operation(s) for teams.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Namely MCP tool candidate](https://apis.io/servers/namely/namely-mcp-tool-candidate/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Namely Api Overlay](https://apis.io/overlays/namely/namely-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Namely Authentication](https://apis.io/security/namely/namely-authentication/)
- [Namely Domain Security](https://apis.io/security/namely/namely-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Namely Plans Pricing](https://apis.io/plans/namely/namely-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Namely Rate Limits](https://apis.io/rate-limits/namely/namely-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://namely.com/)
- [Documentation](https://developers.namely.com/)
- [Getting started](https://developers.namely.com/docs/namely-api/72f9086e4f0e7-introduction)
- [API reference](https://developers.namely.com/docs/namely-api/12dab89109ded-namely-api)
- [Pricing](https://namely.com/lp/pricing/)
- [Support](https://namely.com/employee-support/)
- [Blog](https://namely.com/blog/)
- [Terms of service](https://namely.com/tos/)
- [Privacy policy](https://namely.com/privacy/)
- [GitHub](https://github.com/namely)
- [Status](https://status.namely.com/)

## API Evangelist rating

**Kin Score 56.4** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 43.9 |
| Contract governance | 18.2 |
| Operational transparency | 55.3 |
| Developer ergonomics | 73.2 |
| Access clarity | 69.7 |

**Agent readiness 25.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | partial |
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

**Regulatory alignment 24.5** — Employment & Payroll

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/namely/](https://apis.io/providers/namely/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Namely: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/namely/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
