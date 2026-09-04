# Archived specs

`appomni-openapi-scaffold-2026-05.yaml` is the four-operation scaffold this repo carried before
2026-09-04. It was authored from AppOmni marketing prose, not harvested: it declared a base URL of
`https://api.appomni.com/v1` (that host is AppOmni's public **Postman documenter**, not an API host)
and paths `/events`, `/policies`, `/compliance/reports` that AppOmni does not serve.

It is retained only as a provenance record. The specs in `openapi/` are now derived operation-by-operation
from AppOmni's own published public Postman collection at https://api.appomni.com/ and from the source of
AppOmni's published `@appomni/n8n-nodes-agentguard` package. Do not re-register this file.
