---
name: appomni-triage-posture-findings
description: Triage AppOmni Posture Findings — list open findings, inspect an occurrence, assign an owner, close by exception, and restore if the exception was wrong.
api: appomni:appomni-security-events-api
openapi: openapi/appomni-security-events-api-openapi.yml
operations:
  - listFindings
  - getFindingDetails
  - getFindingOccurrences
  - findingOccurrencesDetailView
  - assignFindings
  - updateFindingOccurrenceDetailedStatusByOccurrenceIDs
  - closeOccurrenceByException
  - closeOccurrenceByExceptionByFilter
  - restoreAnOccurrence
  - restoreOccurrencesByFilter
generated: '2026-09-04'
method: generated
source: openapi/appomni-security-events-api-openapi.yml + conventions/appomni-conventions.yml
---

# Triage AppOmni Posture Findings

Posture Findings is AppOmni's consolidated view of policy issues and Insights. A **finding** is the
problem; an **occurrence** is one instance of it on one object in one monitored service. You close
occurrences, not findings.

## Before you start

- Base URL is `https://{instance}.appomni.com` — the customer's own subdomain. There is no shared host.
- Auth: `Authorization: Bearer <token>` from Settings > API Settings.
- Every list endpoint is limit/offset paginated: `?limit=50&offset=0`, with `?ordering=` and `?search=`.
- **There is no idempotency mechanism.** Do not blind-retry a failed PATCH — re-read the occurrence and
  check its status first.
- Watch the `X-RateLimit: <used>/<limit>` response header. The observed limit is 2000. AppOmni publishes
  no reset timestamp and sends no `Retry-After`, so back off on your own clock.

## Steps

1. **List open findings.** `listFindings` — `GET /api/v1/findings/finding/`. Page with `limit`/`offset`.
   Narrow with the query parameters the spec declares (service, criticality, status) rather than pulling
   everything.
2. **Scope it to real services.** `listServiceIDs` — `GET /api/v1/findings/finding/service_ids` tells
   you which monitored services actually carry findings, so you do not iterate over services with none.
3. **Read the finding.** `getFindingDetails` — `GET /api/v1/findings/finding/{id}/`.
4. **Enumerate its occurrences.** `getFindingOccurrences` — `GET /api/v1/findings/occurrence/`, then
   `findingOccurrencesDetailView` — `GET /api/v1/findings/occurrence/{occurrence_id}/` for one.
5. **Assign an owner.** `assignFindings` — `PATCH /api/v1/findings/finding/assign/`.
6. **Move status.** `updateFindingOccurrenceDetailedStatusByOccurrenceIDs` —
   `PATCH /api/v1/findings/occurrence/update_detailed_status/` for an explicit id list, or
   `updateFndingOccurrenceDetailedStatusByFilter` (`.../update_detailed_status_by_filter/`) to move a
   whole filtered set at once.
7. **Accept the risk.** `closeOccurrenceByException` —
   `PATCH /api/v1/findings/occurrence/close_by_exception/`, or the `_by_filter` variant for a set.

## Undoing step 7

This is the one thing to get right. `close_by_exception` is **reversible**:

- `restoreAnOccurrence` — `PATCH /api/v1/findings/occurrence/restore/`
- `restoreOccurrencesByFilter` — `PATCH /api/v1/findings/occurrence/restore_by_filter/`

AppOmni does **not** publish a window inside which restore works. Treat it as best-effort, not
guaranteed, and never tell a user "you can undo this within N days" — that number does not exist.

Prefer the id-list variants over the `_by_filter` variants when a human is going to review the result.
A filter-scoped close can move far more occurrences than the operator expected, and the filter that
selected them is not stored with the change.

## Errors

Errors come back as the Django REST Framework envelope `{"detail": "..."}` — **not** RFC 9457
problem+json. A 403 means the token's AppOmni user lacks the permission, not that the object is missing;
`getCurrentUserSPermissionsForPolicyIssues` (`GET /api/v1/{service_type}/ruleevent/meta/`) returns the
caller's `list/create/update/partial_update/delete` flags, so check before you write.
