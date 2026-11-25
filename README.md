# nz-djs

Monorepo for two New Zealand music directories:

- `packages/kiwi-djs` — open directory of Aotearoa DJs, mixes, events and venues.
- `packages/kiwi-fests` — open directory of NZ music festivals, promoters and artists.

Both apps are Next.js 16 + TypeScript + Tailwind, share one pnpm lockfile, and
are driven from the workspace root with Turborepo.

## Quick start

```bash
pnpm install
pnpm dev
```

`pnpm dev` starts both apps. Each package reads its own `.env.local`; copy
`packages/<name>/.env.example` before running a package that needs a database.

## Commands

| Command | Scope |
| --- | --- |
| `pnpm dev` | Both apps in watch mode |
| `pnpm build` | Build both apps |
| `pnpm lint` | ESLint both packages |
| `pnpm typecheck` | TypeScript both packages |
| `pnpm test` | Vitest both packages |
| `pnpm test:coverage` | Coverage both packages |
| `pnpm check` | Each package's full gate |
| `pnpm --filter kiwi-djs <script>` | One package |
| `pnpm --filter kiwi-fests <script>` | One package |

## Layout

```
packages/
  kiwi-djs/     # DJ directory
  kiwi-fests/   # festival directory
docs/
  adr/          # architecture decisions
  agents/       # issue tracker and domain-doc rules
GLOSSARY-MAP.md # points at each package glossary
```

Package-level `AGENTS.md`, `CLAUDE.md` and docs stay with their package. Root
rules in `AGENTS.md` and `CODING_STANDARDS.md` win where they conflict.

## CI

`.github/workflows/ci.yml` is the canonical gate. Package-level `.github`
directories were carried over from the standalone repos and are not read by
GitHub in a monorepo.
