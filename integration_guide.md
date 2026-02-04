# integration_guide.md
# WEDE SDK Integration Guide (Developer Onboarding)

## Goal
Integrate WEDE into an existing platform without changing your application flow. WEDE adds a continuity layer so operations can complete during:
- Network degradation and intermittent connectivity.
- Cloud or CDN outages and centralized dependency failures.
- Congestion and partial regional disruptions.

This guide focuses on safe integration patterns and public contracts only. The proprietary Continuity Engine remains internal (patent pending).

## Quick Start Checklist
1) Identify 2 to 3 critical operations
   - Example: order placement, payment confirmation, driver assignment, appointment confirmation.

2) Add WEDE SDK and configure credentials
   - Use sandbox credentials first.
   - Keep secrets outside source control.

3) Implement idempotency and stable operation IDs
   - Ensure every operation can be retried safely.

4) Wire minimal payload contracts
   - Send only what is necessary to complete the operation.

5) Implement result handling
   - Map WEDE status to your existing UI states without redesign.

6) Run the integration simulator and contract tests
   - Validate behavior under offline, degraded, and outage conditions.

## Integration Modes
### Mode A: Client SDK (Mobile or Edge)
Best for apps where the user device experiences the degradation directly.

What you implement:
- SDK initialization
- Operation submission
- Status handling

### Mode B: Backend SDK (Server)
Best for platforms that centralize business operations on your server.

What you implement:
- Server-side operation submission
- Webhook or polling for status updates
- Observability hooks

### Mode C: Hybrid
Client submits intent, backend confirms completion. This keeps UX responsive while maintaining server authority.

## Required Concepts
### Stable Operation ID
A deterministic identifier for a business action.
- Example: `checkout:{user}:{cart_hash}:{timestamp_bucket}`

### Idempotency Key
A unique key that ensures repeated submissions do not duplicate outcomes.
- Recommended: match your operation_id or a derived stable hash.

### TTL and Attempts
- ttl_seconds: how long the operation remains valid.
- max_attempts: cap retries to avoid abuse and unexpected loops.

## Recommended Payload Rules
- Minimal: include only what is necessary for your operation.
- Validated: enforce a strict schema before sending.
- Pseudonymous: avoid raw PII where possible.
- Deterministic: avoid non-repeatable randomness for idempotent operations.

## Typical Flow
1) User triggers an action (existing flow)
2) Your app or backend creates a Continuity Request
3) SDK validates and submits
4) You receive a status result
5) Your app continues its existing flow:
   - immediate success if delivered quickly
   - “processing” if queued
   - final confirmation when reconciled after an outage


## Status Handling Pattern
- accepted: request received, safe to proceed to “processing”
- queued: waiting for continuity completion, show “processing”
- delivered: operation completed, show “confirmed”
- reconciled: operation completed after an outage, show “confirmed”
- failed: operation did not complete, show “try again” with a safe retry

## Webhooks vs Polling
Choose one:
- Webhooks: recommended for server-side integrations, lower latency.
- Polling: acceptable for simpler pilots, ensure backoff and caps.

## Local Testing and Simulation
This repository includes tools to demonstrate maturity:
- Contract tests for requests and responses.
- A connectivity state simulator with scenarios:
  - online
  - degraded
  - offline
  - cloud outage simulation (API dependency fails)
  - CDN outage simulation (static and auth dependencies fail)

Run recommendations:
- Validate idempotency with repeated submissions.
- Validate TTL behavior.
- Validate that your UI state machine does not break under delayed completion.

## Security Requirements
You are responsible for secure integration:
- Use TLS for all communications.
- Store credentials in secret managers, never in code.
- Apply least privilege roles.
- Enforce payload validation and schema constraints.
- Implement client-side and server-side rate limiting where applicable.

Security baseline supported by WEDE enterprise deployments:
- TLS 1.2+/1.3, HTTPS
- OAuth 2.0 / OIDC, JWT short-lived, PKCE
- RBAC, ABAC
- AES-256 at rest
- HMAC-SHA256, SHA-256
- MFA/TOTP where applicable
- Anti-replay measures
- Idempotency keys
- Payload validation
- Rate limiting
- Audit logs
