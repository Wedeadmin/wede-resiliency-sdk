# roadmap_status.md

# wede engineering roadmap and status

## Scope of this roadmap

This roadmap describes the public SDK/API layer and supporting tooling for early adopters.

It does not describe or disclose wede’s proprietary continuity engine, routing logic, or reconciliation internals.

The goal is to show integration readiness, release discipline, onboarding maturity, and product progress for engineering teams evaluating sandbox integration or pilot deployment.

## Current status summary

- product: offline-first continuity infrastructure integrated via API/SDK
- public repo purpose: developer onboarding, contract testing, simulator support, reference integrations, and early pilot readiness
- proprietary core: internal and protected, not shipped in this repository

### Target users

- engineering teams operating platforms in emerging markets with limited or expensive connectivity
- engineering teams needing resilience against cloud, CDN, and centralized dependency outages
- product and platform teams evaluating continuity for critical workflows

## Milestones

### Milestone 0: public repository baseline
Status: completed

Delivered:

- documentation structure established
- licensing clarified for the public layer
- contribution boundaries defined to protect core IP
- separation between public contracts and proprietary logic made explicit
- security posture summary and integration guardrails published

### Milestone 1: contract-first SDK surface
Status: in progress

Objective:

- provide a stable set of public interfaces and models for continuity operations

Work items:

- typed request and response models
- idempotency and TTL helpers
- provider adapter interface definitions
- error taxonomy and retry semantics

Acceptance criteria:

- deterministic behavior for repeated submissions using idempotency keys
- contract tests cover schema validation, error mapping, and version compatibility

### Milestone 2: integration tooling and simulator
Status: in progress

Objective:

- provide reproducible validation for online, degraded, offline, and outage scenarios

Work items:

- connectivity state simulator
- dependency failure simulation
- deterministic fixtures for CI
- test scenarios for delayed completion and safe retry behavior

Acceptance criteria:

- CI runs contract tests and simulation scenarios
- sample integrations pass under all scenarios without changing app flows

### Milestone 3: reference integrations
Status: planned

Objective:

- demonstrate flow-preserving integration patterns across typical stacks

Planned examples:

- marketplace checkout
- dispatch and assignment confirmation
- health appointment confirmation
- fintech transaction confirmation

Acceptance criteria:

- each sample shows stable `operation_id` strategy
- each sample uses idempotency correctly
- each sample maps status handling to existing UI logic
- each sample exposes non-sensitive observability hooks

### Milestone 4: provider adapter stubs
Status: planned

Objective:

- provide clean adapter boundaries without embedding routing logic

Planned:

- mock provider for local development
- enterprise adapter template
- minimal transport abstraction

Acceptance criteria:

- adapters remain pluggable
- adapters do not expose internal routing strategies

### Milestone 5: release discipline
Status: planned

Objective:

- make the public SDK/API layer reliable for pilot integrations and early production preparation

Planned:

- semantic versioning
- changelog discipline
- backward compatibility policy
- deprecation windows for breaking changes

Acceptance criteria:

- tagged releases
- documented migration paths
- predictable interface evolution

## Engineering governance

- branching: `main` for stable releases, feature branches for active work
- CI: contract tests, simulator scenarios, linting, dependency scanning
- security: no secrets in repo, mandatory review for interface changes
- IP protection:
  - no core decision logic
  - no routing heuristics
  - no reconciliation internals
  - no production provider configurations

## What engineering teams can evaluate in this repository

- onboarding clarity
- contract quality
- integration workflow
- simulation discipline
- release discipline
- separation between public interfaces and proprietary logic
- evidence of resilience thinking under degraded conditions

## Near-term priorities

- finalize contract models and error taxonomy
- publish simulator scenarios for degraded and outage conditions
- ship 1 to 2 reference integrations
- stabilize the SDK/API surface for early adopters

## Medium-term priorities

- expand reference integrations
- add enterprise adapter templates
- improve observability hooks and metrics exports
- formalize backward compatibility policy

## Commercial note

This repository is not a free version of the full wede enterprise system.

wede is licensed and paid for B2B and B2G deployments.

This public repository exists to support safe integration, developer onboarding, sandbox evaluation, and pilot adoption while preserving proprietary technology and patent-pending IP.
