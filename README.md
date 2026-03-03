# wede resiliency sdk

**Proof of Continuity layer for DePIN and critical digital infrastructure.**

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](./LICENSE)
[![Status](https://img.shields.io/badge/Status-Active_Development-green.svg)](./roadmap_status.md)

## Overview
wede is an offline-first resiliency middleware that helps connected systems remain operational during connectivity degradation and infrastructure disruptions, including cloud or CDN outages.

This repository contains the public, open-source integration surface and reference components intended for technical evaluation and engineering due diligence across multiple infrastructure and ecosystem programs. wede’s proprietary continuity engine and internal decision logic are excluded and remain protected (patent pending).

## What wede enables
wede provides a continuity layer that allows systems to:
1. **Buffer** data locally when connectivity degrades or fails.
2. **Sign and sequence** data packets using chain-native or system-native identity standards (deployment dependent).
3. **Settle** verifiable Proof of Continuity batches once connectivity is restored, enabling auditability and post-outage reconciliation.

This approach is relevant for emerging markets where connectivity can be limited or expensive, and for highly connected markets exposed to systemic dependency chains and cloud or CDN outages.

## Supported architectures (active integrations)
### 1) Polkadot and peaq ecosystem (Substrate)
- **Native integration:** `pallet-wede` (in development)
- **Target:** High-trust DePIN use cases such as maritime, agriculture, and mobility on peaq

### 2) Arbitrum and EVM (Orbit chains)
- **Native integration:** Solidity smart contracts and Stylus (Rust)
- **Target:** High-frequency verified sensor networks and resilient settlement on Arbitrum Orbit chains

## Strategic roadmap (high-value integrations)
To reach chain-agnostic resiliency and broader deployment options, wede is initiating development for:
- **IoTeX (W3bstream):** Integration with Trusted Execution Environments (TEE) for high-assurance device attestation and continuity proofs
- **ICP (Internet Computer):** Leveraging canister smart contracts for decentralized storage and verification of large offline datasets

## Technical architecture (public view)
The SDK is structured around two main modules:

- **`wede-client`**  
  An embedded Rust library (`no_std`) designed for edge devices (for example ESP32 and Raspberry Pi). It handles local buffering, sequencing, and cryptographic signing under degraded or offline conditions.

- **`wede-verifier`**  
  On-chain or verifiable logic that validates ordering, signatures, and integrity of reconnected data batches once connectivity is restored.

This repository intentionally excludes wede’s proprietary continuity engine, routing strategies, reconciliation logic, production provider configurations, and operational risk controls.

## Documentation
- `architecture_specs.md`  Public system logic overview
- `integration_guide.md`   Developer onboarding and integration patterns
- `roadmap_status.md`      Engineering progress and maturity signals

## Security baseline (public summary)
wede enterprise deployments follow a Zero Trust posture and support:
- TLS 1.2+/1.3, HTTPS
- OAuth 2.0 / OpenID Connect, short-lived JWT, PKCE (where applicable)
- RBAC and ABAC
- AES-256 at rest
- HMAC-SHA256 and SHA-256
- MFA/TOTP (where applicable)
- Anti-replay measures (nonces, timestamps, IDs)
- Idempotency keys for safe retries
- Payload validation
- Rate limiting and audit logs

This repository contains no secrets, provider credentials, routing tables, or production execution logic.

## Commercial model
wede is licensed and paid (B2B, B2G). This open-source repository exists to enable safe integration evaluation, developer onboarding, and engineering due diligence, while preserving patent-pending intellectual property.

## Contribution policy
Contributions are welcome for:
- Documentation improvements
- Contract tests and fixtures
- Simulator and tooling enhancements
- Reference integrations that do not expose sensitive logic

Do not submit:
- Core decision or routing logic
- Reconciliation heuristics or scoring strategies
- Production provider configurations
- Any material that could compromise patent-pending IP

## License
Licensed under the Apache License, Version 2.0. See [LICENSE](./LICENSE).

## Contact
For Private Beta access or integration inquiries, contact: `geral@wede.pt`
