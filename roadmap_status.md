# roadmap_status.md
# WEDE Engineering Roadmap and Status (Open Source Layer)

## Scope of This Roadmap
This roadmap describes the open-source integration layer and supporting tooling. It does NOT describe or disclose WEDE’s proprietary Continuity Engine (patent pending). The goal is to provide reviewers a clear picture of engineering progress, governance, and release discipline.

## Current Status Summary
- Product: Offline-first continuity infrastructure integrated via API/SDK.
- Open-source repo purpose: integration maturity proof, developer onboarding, contract testing, and reference adapters.
- Proprietary core: internal and protected, not shipped in this repository.

Target users:
- Engineering teams operating platforms in emerging markets with limited or expensive connectivity.
- Engineering teams needing resilience against cloud, CDN, and centralized dependency outages.

## Milestones
### Milestone 0: Repository Compliance Baseline (Completed)
- Documentation structure established:
  - architecture_specs.md
  - integration_guide.md
  - roadmap_status.md
- Licensing clarified for the open-source layer.
- Contribution boundaries defined to protect core IP.

Deliverables:
- Clear separation between public contracts and proprietary logic.
- Security posture summary and integration guardrails.

### Milestone 1: Contract-First SDK Surface (In Progress)
Objective:
- Provide a stable set of public interfaces and models for continuity operations.

Work items:
- Typed request/response models for continuity operations
- Idempotency and TTL enforcement helpers
- Provider adapter interface definitions
- Error taxonomy and retry semantics

Acceptance criteria:
- Deterministic behavior for repeated submissions using idempotency keys
- Contract tests cover:
  - schema validation
  - error mapping
  - version compatibility

### Milestone 2: Integration Tooling and Simulator (In Progress)
Objective:
- Provide reproducible tests for offline, degraded, and outage scenarios.

Work items:
- Connectivity state simulator (online, degraded, offline)
- Dependency failure simulation (cloud API failure, CDN/auth dependency failure)
- Deterministic fixtures for CI

Acceptance criteria:
- CI runs contract suite and simulation scenarios
- Sample integrations pass under all scenarios without changing app flows

### Milestone 3: Reference Integrations (Planned)
Objective:
- Demonstrate flow-preserving integration patterns across typical stacks.

Planned examples:
- Marketplace checkout
- Dispatch and assignment confirmation
- Health appointment confirmation
- Fintech transaction confirmation

Acceptance criteria:
- Each sample shows:
 - stable operation_id strategy
 - idempotency usage
 - status handling with existing UI logic
 - observability hooks (non-sensitive metrics)

### Milestone 4: Provider Adapter Stubs (Planned)
Objective:
- Provide clean adapter boundaries without embedding routing logic.

Planned:
- Mock provider (local)
- Enterprise adapter template
- Minimal transport abstraction

Acceptance criteria:
- Adapters remain pluggable and do not expose internal routing strategies

### Milestone 5: Release Discipline (Planned)
Objective:
- Make the open-source layer credible for production integration evaluation.

Planned:
- Semantic versioning and changelog
- Backward compatibility policy
- Deprecation windows for breaking changes

Acceptance criteria:
- Tagged releases
- Documented migration paths

## Engineering Governance
- Branching: main for stable releases, develop for integration work
- CI: contract tests, simulator scenarios, linting, dependency scanning
- Security: no secrets in repo, mandatory reviews for interface changes
- IP protection:
  - No core decision logic
  - No routing heuristics
  - No reconciliation internals
  - No production provider configs

## What Reviewers Can Evaluate (Without Core Disclosure)
- Maturity of contracts, tests, and docs
- Integration workflow quality and onboarding clarity
- Architectural separation of concerns
- Evidence of resilience thinking (degradation, cloud/CDN outages)
- Evidence of correct engineering practices (versioning, CI, security controls)

## Near-Term Priorities (Next 2 to 4 Weeks)
- Finalize contract models and error taxonomy
- Ship simulator scenarios for degraded and outage conditions
- Publish 1 to 2 reference integrations
- Stabilize SDK API surface for grant reviewers

## Medium-Term Priorities (Next 1 to 2 Quarters)
- Expand reference integrations
- Add enterprise adapter templates
- Improve observability hooks and non-sensitive metrics exports
- Formalize backward compatibility policy

## Notes on Commercial Model
This open-source layer is not a free offering of WEDE’s enterprise system. WEDE is licensed and paid (B2B, B2G). This repository exists to enable safe integration evaluation and demonstrate engineering maturity while protecting proprietary technology and patent-pending IP.
