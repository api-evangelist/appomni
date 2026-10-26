# AppOmni (appomni)

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

AppOmni is a SaaS and AI security platform (SSPM) that gives security teams continuous visibility into
the posture, identities, third-party connections and data exposure of the SaaS applications that run an
enterprise — Salesforce, Microsoft 365, Google Workspace, Slack, ServiceNow, Okta, Workday, GitHub, Box,
Zoom, and custom applications built on the AppOmni Developer Platform.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/appomni/refs/heads/main/apis.yml)

## Where the contract came from

AppOmni does **not** publish an OpenAPI document. Its machine-readable contract is a **public Postman
collection**, served at [https://api.appomni.com/](https://api.appomni.com/) (Postman Documenter,
`publishedId` `2sBXc7Mjib`, published 2026-02-04) — 144 requests across 18 product areas with 127 saved
example responses.

That collection is saved here verbatim at
[collections/appomni-api.postman_collection.json](collections/appomni-api.postman_collection.json), and
the nine OpenAPI 3.1.0 documents in `openapi/` were derived from it operation by operation — 132
operations, every path, method, parameter, request body and example response taken from AppOmni's own
document. One further operation, the AgentGuard prompt-classification endpoint, is derived from the
source of AppOmni's own published npm package `@appomni/n8n-nodes-agentguard`.

> **Correction, 2026-09-04.** This repository previously carried a four-operation OpenAPI that was
> authored from AppOmni marketing prose rather than harvested. It declared a base URL of
> `https://api.appomni.com/v1` — that host is AppOmni's Postman documenter, not an API host — and paths
> (`/events`, `/policies`, `/compliance/reports`) that AppOmni does not serve. It has been archived to
> [openapi/_archive/](openapi/_archive/) as a provenance record and is no longer registered. The JSON
> Schema, JSON Structure, example, JSON-LD context and vocabulary built on that fabricated model were
> rebuilt from AppOmni's real response bodies at the same time.

**Base URL:** `https://{instance}.appomni.com` — every customer calls the API on their own AppOmni
subdomain. There is no shared multi-tenant API host. Note that `*.appomni.com` is a wildcard that answers
`200` with an SPA login shell for any unknown subdomain, so a `200` alone does not prove a tenant, a docs
host or an MCP endpoint exists.

## APIs Covered

| API | Operations | Spec |
|---|---|---|
| AppOmni Posture Findings API | 12 | [openapi/appomni-security-events-api-openapi.yml](openapi/appomni-security-events-api-openapi.yml) |
| AppOmni Policies API | 23 | [openapi/appomni-policies-api-openapi.yml](openapi/appomni-policies-api-openapi.yml) |
| AppOmni Compliance and Reports API | 9 | [openapi/appomni-compliance-api-openapi.yml](openapi/appomni-compliance-api-openapi.yml) |
| AppOmni Monitored Services API | 22 | [openapi/appomni-monitored-services-api-openapi.yml](openapi/appomni-monitored-services-api-openapi.yml) |
| AppOmni Identity and Access API | 24 | [openapi/appomni-identity-api-openapi.yml](openapi/appomni-identity-api-openapi.yml) |
| AppOmni SCIM 2.0 API | 5 | [openapi/appomni-scim-api-openapi.yml](openapi/appomni-scim-api-openapi.yml) |
| AppOmni Discovery, Insights and Audit API | 11 | [openapi/appomni-discovery-insights-api-openapi.yml](openapi/appomni-discovery-insights-api-openapi.yml) |
| AppOmni Developer Platform API | 24 | [openapi/appomni-developer-platform-api-openapi.yml](openapi/appomni-developer-platform-api-openapi.yml) |
| AppOmni AI API | 2 | [openapi/appomni-ai-api-openapi.yml](openapi/appomni-ai-api-openapi.yml) |

## What an agent needs to know

- **Auth** — `Authorization: Bearer <token>` from Settings > API Settings. AgentGuard and the Developer
  Platform ingest endpoint use `X-AppOmni-Ingest-Token` instead. OAuth 2.0 refresh-token grant with
  RFC 7662 introspection and RFC 7009 revocation. See
  [authentication/](authentication/appomni-authentication.yml).
- **No idempotency.** Zero occurrences of `idempot` across the whole published surface — there is no
  `Idempotency-Key` header and no documented retry-safety guarantee on any of the 69 mutating operations.
- **Reversibility is real but unbounded.** `restore`, `restore_by_filter`, `bulk_restore` and
  `disable_breakglass` genuinely undo their counterparts, but AppOmni publishes no window inside which a
  reversal works. `DELETE /rule/bulk_delete/` has no restore path at all. See
  [conventions/](conventions/appomni-conventions.yml).
- **Rate limits** — a single `X-RateLimit: <used>/<limit>` response header, observed limit 2000. No
  `Retry-After`, no reset timestamp, no published window. See [rate-limits/](rate-limits/appomni-rate-limits.yml).
- **Errors** — the Django REST Framework envelope `{"detail": "..."}`, not RFC 9457.
- **MCP** — AppOmni publishes AskOmni as an MCP server, but it runs inside the customer's tenant and no
  public endpoint or tool list is published. See [mcp/](mcp/appomni-mcp.yml).
- **No `/.well-known/` document** is served on any AppOmni host. See
  [well-known/](well-known/appomni-well-known.yml).

## Artifacts

| Artifact | Path |
|---|---|
| Postman collection (verbatim, first-party) | [collections/appomni-api.postman_collection.json](collections/appomni-api.postman_collection.json) |
| OpenAPI (9 specs, 132 operations) | [openapi/](openapi/) |
| Overlays | [overlays/](overlays/) |
| Agent Skills | [skills/_index.yml](skills/_index.yml) |
| Agentic access contracts | [agentic-access/appomni-agentic-access.yml](agentic-access/appomni-agentic-access.yml) |
| MCP server + tool crosswalk | [mcp/](mcp/) |
| llms.txt | [llms/appomni-llms.txt](llms/appomni-llms.txt) |
| Authentication | [authentication/appomni-authentication.yml](authentication/appomni-authentication.yml) |
| Conventions (idempotency, reversibility, pagination) | [conventions/appomni-conventions.yml](conventions/appomni-conventions.yml) |
| Error catalog | [errors/appomni-problem-types.yml](errors/appomni-problem-types.yml) |
| Rate limits | [rate-limits/appomni-rate-limits.yml](rate-limits/appomni-rate-limits.yml) |
| Plans and pricing | [plans/appomni-plans-pricing.yml](plans/appomni-plans-pricing.yml) |
| Lifecycle, SLA and status | [lifecycle/appomni-lifecycle.yml](lifecycle/appomni-lifecycle.yml) |
| Conformance and compliance | [conformance/appomni-conformance.yml](conformance/appomni-conformance.yml) |
| Data model | [data-model/appomni-data-model.yml](data-model/appomni-data-model.yml) |
| Packages | [packages/appomni-packages.yml](packages/appomni-packages.yml) |
| Domain security | [security/appomni-domain-security.yml](security/appomni-domain-security.yml) |
| Vulnerability disclosure | [security/appomni-vulnerability-disclosure.yml](security/appomni-vulnerability-disclosure.yml) |
| Trust center | [security/appomni-trust-center.yml](security/appomni-trust-center.yml) |
| Well-known probe | [well-known/appomni-well-known.yml](well-known/appomni-well-known.yml) |
| JSON Schema | [json-schema/](json-schema/) |
| JSON Structure | [json-structure/](json-structure/) |
| JSON-LD context | [json-ld/appomni-context.jsonld](json-ld/appomni-context.jsonld) |
| Spectral rules | [rules/](rules/) |
| Vocabulary | [vocabulary/appomni-vocabulary.yaml](vocabulary/appomni-vocabulary.yaml) |
| FinOps | [finops/appomni-finops.yml](finops/appomni-finops.yml) |

## What AppOmni does not publish

No pricing page, no changelog or release notes, no deprecation or sunset policy, no webhooks or AsyncAPI
event surface, no CLI, no embeddable components, no client SDK in any language registry, no `llms.txt`,
no `/.well-known/` documents, and no A2A agent card. Each of those absences is recorded with the URL and
status code that was probed, in the artifact it belongs to.

## Maintainers

**FN:** API Evangelist

**Email:** info@apievangelist.com
