# Mission: Transferable Harness Desktop Integration

[中文](MISSION.md)

## Why

Turn the integration experience proven by DSH Desktop into a repeatable method.
When Qianwen Harness, another agent Harness, or a new Web UI appears, the team
should identify its boundaries first and ship a compatibility-first desktop
product without reimplementing the upstream product.

## Success looks like

- Map the Host, Carrier, Client, Profile, and Native layers after reading a new
  project.
- Choose a thin host, sidecar, static Client, or external-browser pattern from
  evidence.
- Build a compatibility prototype without editing upstream source while
  preserving upstream plugin and data semantics.
- Define runtime closure, security boundaries, recovery behavior, and release
  verification gates.
- Use the repository's `harness-desktop-adapter` Skill draft for the next
  integration.

## Constraints

- Keep upstream source traceable and comparable; desktop behavior belongs to
  separately owned code.
- Start with compatibility presentation. Advanced presentation rests on stable
  carrier and service boundaries.
- Keep builds, type checks, unit tests, and Loader smokes headless-safe.
- Teach in Chinese while retaining necessary English architecture terms and code
  identifiers.

## Out of scope

- Writing concrete adapters for unpublished target Harnesses.
- Reimplementing upstream agent, model, session, or plugin semantics.
- Code signing, app-store review, and production certificate operations.
