# Domain Docs

Engineering skills should consume this repository's domain documentation before exploring or changing behavior.

## Layout

This is a single-context repository:

```text
/
├── CONTEXT.md
├── docs/adr/
└── src/
```

`CONTEXT.md` and `docs/adr/` are created or expanded lazily when domain terms or architectural decisions are resolved. Their absence is not itself a setup error.

## Before exploring

- Read `CONTEXT.md` when it exists.
- Read ADRs under `docs/adr/` that touch the area being changed.
- Use the glossary's established vocabulary in issue titles, plans, tests, and implementation notes.

## ADR conflicts

If a proposed change conflicts with an existing ADR, surface the conflict explicitly instead of silently overriding the decision.
