# WEDE Open Source Integration Surface

WEDE is an offline-first communication infrastructure layer (API/SDK) that helps digital platforms remain operational during network degradation and during cloud or CDN outages.

This repository contains the public, open-source integration surface of WEDE. It is designed to support technical evaluation and engineering due diligence for infrastructure programs and partners, while preserving WEDE’s proprietary core architecture (patent pending).

## What’s in this repository
Open-source components:
- Public SDK contracts (interfaces, models, adapters) for continuity operations
- Reference integration patterns (flow-preserving)
- Local testing tools and a connectivity/outage simulator
- Contract test suite for Engineering Due Diligence

## What’s not in this repository
Protected, internal components (closed-source):
- The proprietary WEDE Continuity Engine (decision logic, routing strategy, reconciliation internals)
- Production provider routing and redundancy configurations
- Operational risk controls, anti-abuse logic, and production playbooks

## Why WEDE (problem context)
Most platforms assume connectivity is binary. In real-world conditions, especially in emerging markets where connectivity can be limited or expensive, networks degrade, fragment, and disappear. In highly connected markets, platforms are still exposed to systemic dependencies such as cloud and CDN outages.

WEDE adds a continuity layer that preserves existing application flows and helps maintain service reliability across fintech, health, logistics, marketplaces, government and NGO use cases.

## Documentation
- `architecture_specs.md`  System logic overview (public view)
- `integration_guide.md`   Developer onboarding and integration patterns
- `roadmap_status.md`      Engineering progress and repo maturity signals

## Quick start
1) Identify 2 to 3 critical operations (example: order confirmation, payment confirmation, dispatch instruction)
2) Implement stable `operation_id` and idempotency keys
3) Integrate the SDK surface and run contract tests
4) Validate behavior using the simulator under:
   - online
   - degraded
   - offline
   - cloud/CDN dependency outage scenarios

## Development and testing
Recommended workflow:
- Run contract tests to validate request/response compatibility
- Use the simulator to reproduce degraded and outage conditions deterministically

> Note: Command examples depend on your stack. Adjust to your tooling once the repo structure is finalized.

## Security baseline (public summary)
WEDE enterprise deployments support a Zero Trust posture with:
- TLS 1.2+/1.3, HTTPS
- OAuth 2.0 / OpenID Connect, JWT short-lived, PKCE (where applicable)
- RBAC, ABAC
- AES-256 at rest
- HMAC-SHA256, SHA-256
- MFA/TOTP (where applicable)
- Anti-replay measures
- Idempotency keys
- Payload validation
- Rate limiting
- Audit logs

This repository contains no secrets, provider credentials, routing tables, or core execution logic.

## Commercial model
WEDE is licensed and paid (B2B, B2G). This open-source repository exists to enable safe integration evaluation and demonstrate engineering maturity while protecting patent-pending IP.

## Contribution policy
Contributions are welcome for:
- Documentation improvements
- Contract tests and fixtures
- Simulator enhancements
- Reference integrations (non-sensitive)

Do not submit:
- Attempts to reproduce core decision logic
- Routing strategies, scoring, reconciliation internals, or production provider configs
- Any content that could compromise patent-pending IP

## IP notice
WEDE core architecture is proprietary and patent pending. The open-source components in this repository are limited to the integration surface and non-sensitive tooling.

Contact
For access to the Private Beta or integration inquiries, please contact
grants@wede.pt
