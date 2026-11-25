# Domain Docs

How the engineering skills should consume this repo's domain documentation.

## Before exploring, read these

- **`GLOSSARY-MAP.md`** at the repo root, then the package glossary it points
  at for the context you are changing.
- **`docs/adr/`**: read ADRs that touch the area you are about to work in.
- Package-local docs under `packages/<name>/docs/` where they exist.

If any of these files do not exist, **proceed silently**. Do not flag their
absence or suggest creating them upfront. `/domain-modeling` creates them
lazily when terms or decisions actually get resolved.

## File structure

Multi-context repo:

```
/
├── GLOSSARY-MAP.md
├── docs/adr/                          ← system-wide decisions
└── packages/
    ├── kiwi-djs/
    │   ├── GLOSSARY.md
    │   └── docs/adr/                  ← context-specific decisions
    └── kiwi-fests/
        ├── GLOSSARY.md
        └── docs/adr/
```

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor
proposal, a hypothesis, a test name), use the term as defined in the relevant
glossary. Do not drift to synonyms the glossary explicitly avoids.

If the concept you need is not in the glossary yet, note it for
`/domain-modeling` rather than inventing language.

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than
silently overriding it:

> _Contradicts ADR-0007 (event-sourced orders), but worth reopening because…_
