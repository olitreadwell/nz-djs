# ADR-0001: One pnpm workspace for both directories

- Status: accepted
- Date: 2026-11-26

## Context

Kiwi DJs and Kiwi Fests began as two standalone Next.js repositories with the
same stack, the same quality gate shape, and overlapping domain data: a DJ can
play a festival, and a festival lineup is a list of artists. Keeping them as
separate repos duplicated dependency upgrades, CI wiring and agent setup.

## Decision

One repository, `nz-djs`, with two packages under `packages/`. pnpm workspaces
own the lockfile. Turborepo runs package scripts. Each package keeps its own
`AGENTS.md`, runtime configuration, data adapters and tests. No cross-package
imports until a second caller proves the shared seam.

## Consequences

- One install and one lockfile.
- CI runs both package gates from the root.
- Package deploys point at the package directory.
- A shared domain package is a later decision, not a precondition.
