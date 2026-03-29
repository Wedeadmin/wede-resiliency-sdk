# Contributing to wede resiliency sdk

Thank you for your interest in contributing to wede.

This repository exists to provide a stable public SDK/API layer and safe tooling that support developer adoption while protecting wede’s proprietary core architecture.

## What contributions are welcome

We welcome contributions that improve the quality and usability of the public layer, including:

- documentation improvements and clarifications
- contract tests and fixtures
- integration simulators and tooling
- safe reference integrations
- bug fixes in public SDK interfaces or adapters

All contributions must respect the boundaries defined below.

## Contribution boundaries

This repository must not include:

- core continuity decision logic
- routing, scoring, or optimization strategies
- reconciliation heuristics or state management internals
- production provider configurations or redundancy tables
- any implementation attempting to replicate or reverse-engineer wede’s proprietary engine

Pull requests that violate these boundaries will be closed.

## Development workflow

1. Fork the repository
2. Create a feature branch
3. Make focused, well-documented changes
4. Add or update tests where applicable
5. Submit a pull request with a clear description of intent

## Coding standards

- keep interfaces minimal and explicit
- avoid unnecessary dependencies
- prefer deterministic behavior for tests and simulators
- do not introduce secrets or credentials into the codebase

## Intellectual property

By submitting a contribution:

- you confirm that you have the right to submit the code
- you agree that your contribution is licensed under the repository’s Apache 2.0 license
- you acknowledge that wede’s core architecture remains proprietary and is not affected by contributions to this repository

## Review process

All pull requests are reviewed for:

- technical correctness
- security implications
- compliance with contribution boundaries
- alignment with the repository’s public SDK/API purpose

We may request changes or clarification before merging.

Thank you for helping improve the wede integration ecosystem.
