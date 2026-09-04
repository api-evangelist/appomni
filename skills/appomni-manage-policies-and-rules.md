---
name: appomni-manage-policies-and-rules
description: Work AppOmni security policies — list policies, inspect and update rules, run a scan, check assessment status, and handle rule-event violations by closing them or converting them to exceptions.
api: appomni:appomni-policies-api
openapi: openapi/appomni-policies-api-openapi.yml
operations:
  - retrievePosturePolicies
  - getPolicy
  - assignTargetTagsToPolicy
  - retrieveSelectedPosturePolicyRuleOptions
  - retrieveRulesForPolicy
  - updatePolicyRule
  - startPolicyScan
  - checkPolicyScanStatusAndResults
  - listOpenPolicyIssues
  - listOpenPolicyViolations
  - closeRuleEventViolation
  - allowRuleEventViolation
  - deleteAnIndividualRuleWithinAPolicy
  - bulkDeleteRulesWithinAPolicy
  - createAPosturePolicySnapshot
generated: '2026-09-04'
method: generated
source: openapi/appomni-policies-api-openapi.yml + conventions/appomni-conventions.yml
---

# Manage AppOmni policies and rules

A **policy** is a named set of **rules** assessed against monitored services. A failing rule raises a
**rule event**. Many rule routes are scoped by `{service_type}` in the path (`salesforce`, `o365`, and
so on) — read the service type off the monitored service first, do not guess it.

## Read before you write

1. `retrievePosturePolicies` — `GET /api/v1/core/policy/`
2. `getPolicy` — `GET /api/v1/core/policy/{id}/`
3. `retrieveRulesForPolicy` — `GET /api/v1/{policy_type}/rule/` (filter with `?policy={policy_id}`)
4. `retrieveSelectedPosturePolicyRuleOptions` — `GET /api/v1/{service_type}/rule/` for the option set a
   rule can take.

## Change

- `updatePolicyRule` — `PATCH /api/v1/{service_type}/rule/{rule_id}/`. PATCH is partial update.
- `assignTargetTagsToPolicy` — `PATCH /api/v1/core/policy/{id}/` to change which services a policy targets.
- `createAPosturePolicySnapshot` — `POST /api/v1/core/policy/snapshot/` before a large edit. This is the
  closest thing AppOmni publishes to a rollback point, and it is worth taking.

## Assess

- `startPolicyScan` — `POST /api/v1/core/policy/{id}/scan/` kicks the assessment off.
- `checkPolicyScanStatusAndResults` — `GET /api/v1/core/policyassessment/check_status/`. Poll this;
  the scan is asynchronous.
- `listTheLastSuccessfulScanTimeForTheActivePoliciesInAGivenMonitor` and
  `listTheLastSuccessfulScanTimeForAllMonitoredServicesOnAGivenActi` tell you how stale the last
  assessment is before you trust its output.

## Handle violations

- `listOpenPolicyIssues` — `GET /api/v1/core/ruleevent/`
- `listOpenPolicyViolations` — `GET /api/v1/{service_type}/ruleevent/{id}/list_instances/`
- `closeRuleEventViolation` — `PATCH /api/v1/{service_type}/ruleevent/close/`
- `allowRuleEventViolation` — `POST /api/v1/{service_type}/ruleevent/convert_to_exception/` turns the
  violation into a standing exception, which suppresses it going forward. This is a policy decision, not
  a cleanup step; get a human to approve it.

## The two destructive operations

`deleteAnIndividualRuleWithinAPolicy` (`DELETE /api/v1/{service_type}/rule/{id}/`) and
`bulkDeleteRulesWithinAPolicy` (`DELETE /api/v1/{service_type}/rule/bulk_delete/`) have **no published
restore route**. Bulk delete is the highest-blast-radius call in the whole AppOmni surface. Take a
`createAPosturePolicySnapshot` first, require explicit human confirmation, and never issue either one
from an unattended agent loop.

## Conventions

Pagination is `?limit=`/`?offset=` with `?ordering=` and `?search=`. Errors are `{"detail": "..."}`.
There is no `Idempotency-Key` support anywhere in this API, so a retried DELETE is a second DELETE.
