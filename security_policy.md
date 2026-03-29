# Security Policy

## Scope

This repository contains the public SDK/API layer of wede.

It is intentionally limited to SDK interfaces, reference components, and non-sensitive tooling used for secure integration, sandbox testing, and pilot adoption.

wede’s proprietary continuity engine, routing logic, reconciliation mechanisms, and production risk controls are not part of this repository and remain protected and internal.

## Supported security practices

wede enterprise deployments follow a Zero Trust security posture.

While this repository does not include production infrastructure, the following baseline principles apply to integrations built using this SDK/API layer:

- TLS 1.2+/1.3 and HTTPS for transport security
- OAuth 2.0 and OpenID Connect where applicable
- short-lived JWT and PKCE for public clients where applicable
- role-based and attribute-based access control
- AES-256 encryption at rest where deployment requires it
- HMAC-SHA256 and SHA-256 for integrity and hashing
- anti-replay protections using nonces, timestamps, and operation identifiers
- idempotency keys to prevent duplicate execution under degraded conditions
- payload validation and strict schema enforcement
- rate limiting and audit logging at service boundaries
- MFA/TOTP support where applicable

This repository does not contain secrets, private keys, provider credentials, routing tables, or production configurations.

## Reporting a vulnerability

If you discover a security issue related to:

- SDK interfaces
- request or response handling
- cryptographic usage in public components
- documentation that could lead to insecure integration patterns

please report it responsibly.

### How to report

Email: `geral@wede.pt`

Include:

- a clear description
- reproduction steps
- affected files or components where applicable

Do not open public GitHub issues for security vulnerabilities.

## Disclosure policy

- valid reports will be acknowledged within a reasonable timeframe
- confirmed issues will be addressed with appropriate fixes or mitigations
- we request a reasonable disclosure window before any public discussion

## Out of scope

The following are explicitly out of scope for this repository:

- proprietary continuity engine internals
- routing strategies, scoring heuristics, or reconciliation logic
- production provider configurations
- customer-specific deployments or secrets

Thank you for helping keep wede integrations secure.
