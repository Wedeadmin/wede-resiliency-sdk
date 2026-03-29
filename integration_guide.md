# integration_guide.md

# wede sdk integration guide

## Goal

Integrate wede into an existing platform without changing your application flow.

wede adds a continuity layer so critical operations can complete during:

- network degradation and intermittent connectivity
- cloud or CDN outages
- centralized dependency failures
- congestion and partial regional disruption

This guide focuses on safe integration patterns and public contracts only.

The proprietary continuity engine remains internal.

## Quick start checklist

### 1. Identify 2 to 3 critical operations

Examples:

- order placement
- payment confirmation
- driver assignment
- appointment confirmation
- field acknowledgement

### 2. Add the wede SDK and configure credentials

- start with sandbox credentials
- keep secrets outside source control
- isolate configuration by environment

### 3. Implement stable operation IDs and idempotency

Every critical operation should be safely retryable.

### 4. Wire minimal payload contracts

Send only the minimum data required to complete the business action.

### 5. Implement result handling

Map wede status values to your existing UI or backend state machine without redesign.

### 6. Run the simulator and contract tests

Validate behavior under online, degraded, offline, and outage conditions.

## Integration modes

### Mode A: client SDK

Best for apps where the user device directly experiences degraded connectivity.

What you implement:

- SDK initialization
- operation submission
- status handling
- local retry-safe UX states

### Mode B: backend SDK

Best for platforms that centralize business operations on their own server.

What you implement:

- server-side operation submission
- webhook or polling status updates
- observability hooks
- retry-safe completion handling

### Mode C: hybrid

Client submits intent, backend confirms final completion.

This mode keeps UX responsive while preserving server authority.

## Required concepts

### Stable operation ID

A deterministic identifier for a business action.

Example:

`checkout:{user}:{cart_hash}:{timestamp_bucket}`

### Idempotency key

A unique key that ensures repeated submissions do not duplicate outcomes.

Recommended approach:

- reuse the `operation_id`, or
- derive a stable hash from the business action

### TTL and attempts

- `ttl_seconds` defines how long an operation remains valid
- `max_attempts` caps retries to avoid abuse and retry loops

## Recommended payload rules

Payloads should be:

- minimal
- validated
- pseudonymous where possible
- deterministic for safe retries

## Typical flow

1. User triggers an action in the existing flow
2. Your app or backend creates a continuity request
3. SDK validates and submits the request
4. You receive a continuity status result
5. Your app continues its existing flow

Possible UI outcomes:

- immediate confirmation if delivered quickly
- processing state if queued
- final confirmation if reconciled after disruption
- safe retry path if failed

## Status handling pattern

- `accepted`: request received, safe to move into processing
- `queued`: waiting for continuity completion, keep processing state
- `delivered`: operation completed successfully
- `reconciled`: operation completed after delayed recovery
- `failed`: operation did not complete, allow safe retry

## Webhooks vs polling

Choose one based on integration maturity.

### Webhooks

Recommended for server-side integrations with lower latency and cleaner event handling.

### Polling

Acceptable for simpler pilots.
Use backoff and bounded retries.

## Local testing and simulation

This repository may include tooling for:

- contract tests for request and response validation
- connectivity state simulation
- cloud outage simulation
- CDN or dependency failure simulation
- deterministic fixtures for repeatable validation

Recommended validation:

- repeat submissions with the same idempotency key
- TTL expiry behavior
- delayed completion scenarios
- UI state transitions under degraded conditions

## Security requirements

You are responsible for secure integration.

Minimum expectations:

- use TLS for all communications
- store credentials in secret managers, never in code
- apply least-privilege roles
- enforce payload validation and schema constraints
- implement rate limiting where applicable

### Security baseline supported by wede enterprise deployments

- TLS 1.2+/1.3
- HTTPS
- OAuth 2.0 / OIDC where applicable
- short-lived JWT and PKCE where applicable
- RBAC and ABAC
- AES-256 at rest
- HMAC-SHA256 and SHA-256
- MFA/TOTP where applicable
- anti-replay protections
- idempotency keys
- payload validation
- rate limiting
- audit logs

## Recommended first pilot

A strong first pilot usually starts with:

- 1 to 3 critical operations
- one platform environment
- sandbox first, production later
- clear KPIs for acceptance rate, delayed completion, reconciliation success, and retry safety

## Next step

For sandbox access, integration support, or pilot discussions, contact:

`geral@wede.pt`
