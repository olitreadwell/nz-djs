<!-- generated-by: coding-standards ensure -->
# Coding standards: nz-djs

Project rules for this monorepo. The global baseline is
`~/.agents/standards/CODING_STANDARDS.md` and applies unless this file
adds a stricter rule. Read `AGENTS.md` for layout and package scope.

## Stack

- Language and framework: TypeScript, Next.js 16
- Package manager: pnpm workspaces
- Test tools: Vitest, Playwright
- Lint: `pnpm run lint`
- Typecheck: `pnpm run typecheck`

## Commands

- Full gate: `pnpm run check`
- Tests: `pnpm run test`
- Typecheck: `pnpm run typecheck`
- Build: `pnpm run build`

## Test-first in this repo

- Start with a failing test at the nearest seam in the package you are
  changing. Name the seam in one line before writing it.
- Watch the test fail for the right reason, then write the least code
  that passes it.
- Run the package gate and then the workspace gate before claiming done.
- No test needed for docs, config, dependency bumps, or one-off data
  fixes. Say `no test: <reason>` in the change.
- Never skip, delete, or weaken a test, assertion, type check, or lint
  rule to reach green.

## Conventions

- Each package keeps its own `AGENTS.md`, `CLAUDE.md` and architecture
  notes. Root rules win where they conflict.
- Export names use 2 to 3 domain words (`getDjById`, not `get`).
- One spelling per concept across both packages.
- No `any` or untyped escape hatches. Fix types at the boundary.
- Test files sit next to their source and are named after it.
- Comments explain why, directly above the code they explain.

## Branch names

`<type>/<package>/<kebab-description>/<issue-id>`. Omit the trailing id
when no issue exists.

## Done when

`pnpm run check` passes, or the package-level equivalent does for a
single-package change, and every changed behaviour has a test or a
one-line reason it has none.
