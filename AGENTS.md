# Agent instructions: nz-djs

<!-- coding-standards:begin -->
Project coding rules: `CODING_STANDARDS.md`. Global baseline:
`~/.agents/standards/CODING_STANDARDS.md`. Read both before changing
behaviour.
<!-- coding-standards:end -->

## What this is

A pnpm + Turborepo monorepo for two Next.js 16 directories:

- `packages/kiwi-djs` — DJs, mixes, events and venues.
- `packages/kiwi-fests` — festivals, promoters, artists and lineups.

## Must pass

- Workspace: `pnpm typecheck && pnpm lint && pnpm test`.
- Package gate before a package change: `pnpm --filter <package> check`.

## Package boundaries

- Read the package `AGENTS.md` before editing that package.
- Keep package-local data adapters, routes and scripts inside their package.
- Shared code goes to a package first; promote it to a workspace package only
  when a second caller exists. One adapter is a hypothetical seam.
- Root commands use Turborepo. Do not add package-level lockfiles or
  `turbo.json` files.

## Project facts

- Package manager: pnpm 10.
- Node: 22.22.2 from `.nvmrc`.
- Tests: Vitest per package; Playwright for e2e.
- Issue tracker: GitHub Issues in `olitreadwell/nz-djs`.
