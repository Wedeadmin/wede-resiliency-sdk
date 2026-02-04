# Security Policy

## Scope
This repository contains the public, open-source integration surface of WEDE. It is intentionally limited to SDK interfaces, reference components, and non-sensitive tooling used for integration evaluation and engineering due diligence.

WEDE’s proprietary continuity engine, routing logic, reconciliation mechanisms, and production risk controls are not part of this repository and remain protected and internal (patent pending).

## Supported Security Practices
WEDE enterprise deployments follow a Zero Trust security posture. While this repository does not include production infrastructure, the following baseline principles apply to integrations built using this SDK surface:

- TLS 1.2+/1.3 and HTTPS for transport security
- OAuth 2.0 and OpenID Connect where applicable
- Short-lived JWTs and PKCE for public clients where applicable
- Role-based and attribute-based access control (RBAC, ABAC)
- AES-256 encryption at rest (deployment dependent)
- HMAC-SHA256 and SHA-256 for integrity and hashing
- Anti-replay protections using nonces, timestamps, and operation identifiers
- Idempotency keys to prevent duplicate execution under degraded connectivity
- Payload validation and strict schema enforcement
- Rate limiting and audit logging at service boundaries
- MFA/TOTP support where applicable

This repository does not contain secrets, private keys, provider credentials, routing tables, or production configurations.

## Reporting a Vulnerability
If you discover a security issue related to:
- SDK interfaces
- request or response handling
- cryptographic usage in public components
- documentation that could lead to insecure integration patterns

please report it responsibly.

### How to report
- Email: security@wede.tech  
- Include a clear description, reproduction steps, and affected files if applicable.

Do not open public GitHub issues for security vulnerabilities.

## Disclosure Policy
- Valid reports will be acknowledged within a reasonable timeframe.
- Confirmed issues will be addressed with appropriate fixes or mitigations.
- We request a reasonable disclosure window before any public discussion.

## Out of Scope
The following are explicitly out of scope for this repository:
- WEDE proprietary continuity engine internals
- Routing strategies, scoring heuristics, or reconciliation logic
- Production provider configurations
- Customer-specific deployments or secrets

Thank you for helping keep WEDE integrations secure.
