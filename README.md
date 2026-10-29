# AppOmni

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

AppOmni is a SaaS and AI security platform (SSPM) that gives security teams continuous visibility into the posture, identities, third-party connections and data exposure of the SaaS applications that run an enterprise — Salesforce, Microsoft 365, Google Workspace, Slack, ServiceNow, Okta, Workday, GitHub, Box, Zoom and custom applications built on its Developer Platform. It publishes a tenant-scoped REST API covering posture findings, policies, compliance reporting, monitored services, identity, discovery, insights, SCIM 2.0 provisioning and AI security, plus AskOmni (an MCP server) and AgentGuard runtime prompt protection for agentic AI.

**Areas:** SaaS Security · SSPM · Compliance · Threat Detection · CASB · Zero Trust · Identity · SCIM · AI Security · Posture Management

## AppOmni on APIs.io

Everything profiled for AppOmni is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/appomni/](https://apis.io/providers/appomni/)** — or go straight to one of the APIs or properties below.

### APIs (18)

- [AppOmni Policies API](https://apis.io/apis/appomni/appomni-policies-api/) — Create, read, update and delete AppOmni security policies and the rules inside them, run and inspect policy assessments, and handle rule events — closing…
- [AppOmni Monitored Services API](https://apis.io/apis/appomni/appomni-monitored-services-api/) — Register and administer the SaaS services AppOmni monitors, inspect their data-sync state, rotate ingest tokens, and manage the tenant-wide custom fields,…
- [AppOmni Identity and Access API](https://apis.io/apis/appomni/appomni-identity-api/) — Unified identities that stitch a person's monitored-service accounts together by email, plus AppOmni platform users, limited users, groups, roles,…
- [AppOmni Agent Guard API](https://apis.io/apis/appomni/appomni-agentguard-api/) — AppOmni AgentGuard runtime prompt security — DLP and prompt-firewall classification for AI agent traffic.
- [AppOmni AO Developer Platform API](https://apis.io/apis/appomni/appomni-ao-developer-platform-api/) — The AppOmni Developer Platform (AODP) enables the creation of custom service types allowing you to monitor the security posture of any application,…
- [AppOmni Audit Logs API](https://apis.io/apis/appomni/appomni-audit-logs-api/) — The Audit Logs API from AppOmni — 2 operation(s) for audit logs.
- [AppOmni Authorization Tokens API](https://apis.io/apis/appomni/appomni-authorization-tokens-api/) — The Authorization Tokens API from AppOmni — 7 operation(s) for authorization tokens.
- [AppOmni [Beta] Policy Assessment Stats API](https://apis.io/apis/appomni/appomni-beta-policy-assessment-stats-api/) — THIS FEATURE IS IN BETA - Please contact Customer Success to enable this early access API Provides a granular breakdown of policy assessments across…
- [AppOmni Custom Field Values for a Monitored Service API](https://apis.io/apis/appomni/appomni-custom-field-values-for-a-monitored-service-api/) — The Custom Field Values API accesses the value of the custom field associated with a given monitored service.
- [AppOmni Custom Fields API](https://apis.io/apis/appomni/appomni-custom-fields-api/) — The Custom Fields API controls the tenant-wide fields that can be custom-created and assigned to different monitored services. Note : Delete operations for…
- [AppOmni Discovery API](https://apis.io/apis/appomni/appomni-discovery-api/) — The Discovery API from AppOmni — 3 operation(s) for discovery.
- [AppOmni Insights API](https://apis.io/apis/appomni/appomni-insights-api/) — The Insights API from AppOmni — 6 operation(s) for insights.
- [AppOmni Marlin AI API](https://apis.io/apis/appomni/appomni-marlin-ai-api/) — Marlin AI is an autonomous SaaS security AI that runs platform-wide deep analyses and correlations automatically across security observations in the AppOmni…
- [AppOmni Posture Findings API](https://apis.io/apis/appomni/appomni-posture-findings-api/) — Posture Findings consolidates policy issues and Insights into a single view, allowing you to efficiently manage and resolve alerts. The Posture Findings API…
- [AppOmni Reports API](https://apis.io/apis/appomni/appomni-reports-api/) — The Reports API from AppOmni — 6 operation(s) for reports.
- [AppOmni SCIM User Management API](https://apis.io/apis/appomni/appomni-scim-user-management-api/) — Use SCIM to connect your identity provider to AppOmni, and utilize this API to: - Get all users in a company - Activate or deactivate users - Update a…
- [AppOmni Users and Roles API](https://apis.io/apis/appomni/appomni-users-and-roles-api/) — The Users and Roles API from AppOmni — 7 operation(s) for users and roles.
- [AppOmni Value List API](https://apis.io/apis/appomni/appomni-valuelist-api/) — ValueList and ValueListElement are used to manage lists of items used by Insights. ValueLists have a type designation and will be used by Insights on…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [AskOmni MCP Server](https://apis.io/servers/appomni/askomni-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Appomni Agentic Access](https://apis.io/agentic-access/appomni/appomni-agentic-access/)

#### JSON Schema (4)

The data models the API reads and writes.

- [Finding](https://apis.io/schemas/appomni/appomni-finding/)
- [Occurrence](https://apis.io/schemas/appomni/appomni-occurrence/)
- [PaginatedList](https://apis.io/schemas/appomni/appomni-paginated-list/)
- [Moved to /providers/appomni/](https://apis.io/schemas/appomni/security-event/)

#### JSON Structure (2)

Data models expressed in JSON Structure.

- [Appomni Occurrence Structure](https://apis.io/json-structure/appomni/appomni-occurrence-structure/)
- [Moved to /providers/appomni/](https://apis.io/json-structure/appomni/security-event-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Appomni Context](https://apis.io/jsonld/appomni/appomni-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Appomni Vocabulary](https://apis.io/vocabularies/appomni/appomni-vocabulary/)

#### Examples (2)

Example requests and responses.

- [Appomni Occurrence Example](https://apis.io/examples/appomni/appomni-occurrence-example/)
- [Moved to /providers/appomni/](https://apis.io/examples/appomni/security-event-example/)

#### Collections (3)

Postman and Open Collection request collections.

- [Moved to /providers/appomni/](https://apis.io/collections/appomni/open-appomni-compliance-api/)
- [Moved to /providers/appomni/](https://apis.io/collections/appomni/open-appomni-policies-api/)
- [Moved to /providers/appomni/](https://apis.io/collections/appomni/open-appomni-security-events-api/)

#### Overlays (9)

OpenAPI overlays, including conversational phrasing for each operation.

- [Appomni Ai Api Overlay](https://apis.io/overlays/appomni/appomni-ai-api-overlay/)
- [Appomni Compliance Api Overlay](https://apis.io/overlays/appomni/appomni-compliance-api-overlay/)
- [Appomni Developer Platform Api Overlay](https://apis.io/overlays/appomni/appomni-developer-platform-api-overlay/)
- [Appomni Discovery Insights Api Overlay](https://apis.io/overlays/appomni/appomni-discovery-insights-api-overlay/)
- [Appomni Identity Api Overlay](https://apis.io/overlays/appomni/appomni-identity-api-overlay/)
- [Appomni Monitored Services Api Overlay](https://apis.io/overlays/appomni/appomni-monitored-services-api-overlay/)
- [Appomni Policies Api Overlay](https://apis.io/overlays/appomni/appomni-policies-api-overlay/)
- [Appomni Scim Api Overlay](https://apis.io/overlays/appomni/appomni-scim-api-overlay/)
- [Appomni Security Events Api Overlay](https://apis.io/overlays/appomni/appomni-security-events-api-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [AppOmni — jsonschema rules](https://apis.io/rules/appomni/appomni-jsonschema-spectral-rules/)
- [AppOmni API Rules](https://apis.io/rules/appomni/appomni-spectral-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Appomni Authentication](https://apis.io/security/appomni/appomni-authentication/)
- [Appomni Domain Security](https://apis.io/security/appomni/appomni-domain-security/)
- [Appomni Trust Center](https://apis.io/security/appomni/appomni-trust-center/)
- [Appomni Vulnerability Disclosure](https://apis.io/security/appomni/appomni-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Appomni Plans Pricing](https://apis.io/plans/appomni/appomni-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Appomni Rate Limits](https://apis.io/rate-limits/appomni/appomni-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Appomni Finops](https://apis.io/finops/appomni/appomni-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://appomni.com/)
- [Documentation](https://appomni.com/resources/)
- [API reference](https://api.appomni.com/)
- [Sign up](https://appomni.com/demo-request/)
- [Support](https://appomni.com/support/)
- [Blog](https://appomni.com/article-type/blog/)
- [Security](https://appomni.com/ao-labs-vulnerability-disclosure-policy/)
- [Terms of service](https://appomni.com/terms-of-service/)
- [Privacy policy](https://appomni.com/privacy-policy/)
- [GitHub](https://github.com/appomni)
- [Status](https://status.appomni.com/)

## API Evangelist rating

**Kin Score 56.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 77.5 |
| Contract quality | 68.1 |
| Contract governance | 35.6 |
| Operational transparency | 50.0 |
| Developer ergonomics | 42.3 |
| Access clarity | 50.0 |

**Agent readiness 35.7** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
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
| Pagination Ratio | — |
| Operation Distinctiveness | mostly |

**Regulatory alignment 35.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/appomni/](https://apis.io/providers/appomni/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for AppOmni: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/appomni/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
