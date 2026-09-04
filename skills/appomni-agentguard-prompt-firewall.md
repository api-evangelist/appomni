---
name: appomni-agentguard-prompt-firewall
description: Route an AI agent's prompt through AppOmni AgentGuard for DLP and prompt-firewall classification before it reaches an LLM, and handle the allow/block verdict including user quarantine.
api: appomni:appomni-ai-api
openapi: openapi/appomni-ai-api-openapi.yml
operations:
  - classifyAgentPrompt
  - marlinAIResults
generated: '2026-09-04'
method: generated
source: >-
  openapi/appomni-ai-api-openapi.yml, derived from AppOmni's published
  @appomni/n8n-nodes-agentguard source (github.com/appomni/n8n-nodes-agentguard)
---

# AppOmni AgentGuard prompt firewall

AgentGuard classifies a prompt before it reaches a model and returns an allow or block verdict. It is a
plain HTTP endpoint on the customer's AppOmni tenant — it is **not** the AskOmni MCP server, which is a
separate product.

## Call

`classifyAgentPrompt` — `POST https://{instance}.appomni.com/api/v1/ai/prompts/agents/classify`

Auth is the **ingest token**, not the platform bearer token:

```
X-AppOmni-Ingest-Token: <token>
```

Get it with `getIngestToken` (`GET /api/v1/core/monitoredservice/{ms_id}/get_ingest_token/`) and rotate
it with `rotateIngestToken`. Rotation is irreversible — the old token cannot be recovered.

Body:

```json
{
  "messages": [
    { "role": "user", "content": "<the prompt>", "content_type": "text/plain" }
  ],
  "include_details": false,
  "metadata": {
    "user":    { "id": "...", "username": "...", "email": "...", "principal_type": "..." },
    "session": { "id": "..." },
    "agent":   { "id": "...", "name": "..." },
    "request": { "src_app": "...", "interface": "...", "user_agent": "...", "src_ip": "..." }
  }
}
```

## Handle the verdict

```json
{
  "response_action": "allow" | "block",
  "response_message": "...",
  "scores": { "benign": 0.0, "malicious": 0.0 },
  "block_reasons": ["..."],
  "classifiers": [{ "name": "...", "status": "success|timeout|error|skipped", "duration_ms": 0 }],
  "effective_threshold": 0.0,
  "event_id": "..."
}
```

- `response_action: "block"` — do not forward the prompt. Surface `response_message` to the user and log
  `block_reasons` and `event_id`.
- `response_action: "allow"` — forward it.
- Fail closed or fail open deliberately. A classifier with `status: "timeout"` or `"error"` did not run;
  decide in advance which way you go when AgentGuard itself is unavailable, and write it down.

## User quarantine

If the tenant policy includes a `user_quarantine` classifier, a repeat offender can be locked out after
N strikes in a rolling window. A locked user returns the ordinary `response_action: "block"` shape with
the quarantine reason in `block_reasons`, so no extra branch is needed.

**Set `metadata.user` explicitly.** Identity resolves in the order `id` → `username` → `email`. If you
leave it empty, quarantine scopes to the conversation, and starting a new session resets the strike
count — which is usually not what a security team means by "quarantine".

Strike counts, windows and lock duration are configured server-side per tenant. Nothing in the request
changes them.

## Off-the-shelf

AppOmni publishes `@appomni/n8n-nodes-agentguard` on npm (v0.1.2, 2026-05-22) if you are wiring this into
n8n rather than calling it directly. It has two outputs, Allowed and Blocked.

## Marlin AI

`marlinAIResults` — `GET /api/v1/ai/marlin/plans/analysis/latest/` returns the latest autonomous
platform-wide analysis. Read-only; unrelated to AgentGuard.
