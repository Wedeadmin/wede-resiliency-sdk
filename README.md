# wede resiliency sdk

Built for early integration, sandbox testing, and pilot deployment in mission-critical digital services.

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](./LICENSE)
[![Status](https://img.shields.io/badge/Status-Active_Development-green.svg)](./roadmap_status.md)

## Overview

wede is an offline-first continuity layer that helps digital platforms remain operational when connectivity degrades, when cloud or CDN dependencies fail, or when infrastructure disruptions affect normal service delivery.

This repository provides the public SDK/API surface, reference contracts, safe integration tooling, and onboarding materials needed for early adoption, sandbox testing, and pilot integrations.

wede’s proprietary continuity engine, internal routing logic, reconciliation internals, and production risk controls are not included in this repository and remain protected.

## What wede enables

wede helps platforms:

1. Buffer critical operations safely when connectivity degrades or fails.
2. Preserve application flow without forcing a redesign of core user journeys.
3. Submit deterministic continuity operations with stable identifiers and safe retries.
4. Return consistent operation states such as accepted, queued, delivered, reconciled, or failed.
5. Support post-outage confirmation and reconciliation once dependencies recover.

This approach is relevant for mission-critical systems, for emerging markets where connectivity can be limited or expensive, and for highly connected markets exposed to cloud, CDN, or centralized dependency failures.

## Typical use cases

wede is designed for operations that must not be lost during disruption, including:

- order confirmation
- payment confirmation
- dispatch and assignment workflows
- appointment confirmation
- field operations and service coordination
- critical workflow acknowledgements

## Public architecture

The public SDK/API layer is structured around two main modules:

### `wede-client`
An embedded or platform-side library for creating, validating, buffering, and submitting continuity operations under offline or degraded conditions.

### `wede-verifier`
A verification boundary for validating ordering, integrity, and continuity outcomes when operations complete after disruption or delayed recovery.

This repository intentionally excludes the proprietary continuity engine, routing strategies, reconciliation logic, provider configurations, and internal operational controls.

## Documentation

- `architecture_specs.md` Public system architecture and boundaries
- `integration_guide.md` Developer onboarding and integration patterns
- `roadmap_status.md` Product and engineering maturity for early adopters
- `security_policy.md` Security baseline and vulnerability reporting
- `contributing.md` Contribution rules for the public SDK/API layer

## Security baseline

wede enterprise deployments follow a Zero Trust posture and support:

- TLS 1.2+/1.3
- HTTPS
- OAuth 2.0 / OpenID Connect where applicable
- short-lived JWT and PKCE where applicable
- RBAC and ABAC
- AES-256 at rest
- HMAC-SHA256 and SHA-256
- MFA/TOTP where applicable
- anti-replay measures
- idempotency keys
- payload validation
- rate limiting
- audit logs

This repository contains no secrets, provider credentials, routing tables, or production execution logic.

## Commercial model

wede is licensed and paid for B2B and B2G deployments.

This open repository exists to support developer onboarding, safe integration, sandbox testing, reference implementations, and early pilot adoption while preserving patent-pending intellectual property.

## Contribution policy

Contributions are welcome for:

- documentation improvements
- contract tests and fixtures
- simulators and local tooling
- safe reference integrations
- bug fixes in public interfaces and adapters

Do not submit:

- core continuity decision logic
- routing or scoring strategies
- reconciliation internals
- production provider configurations
- any material that could compromise patent-pending IP

## License

Licensed under the Apache License, Version 2.0.
See [LICENSE](./LICENSE).

## Contact

For sandbox access, pilot discussions, or integration inquiries, contact:

`geral@wede.pt`
