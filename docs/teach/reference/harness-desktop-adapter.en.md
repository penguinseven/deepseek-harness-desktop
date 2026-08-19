# Harness Desktop Adapter Quick Reference

[中文](harness-desktop-adapter.md)

Use this reference to decide within 30 minutes whether a new Harness or Web UI
is suitable for rapid desktop integration and to identify the smallest adapter.

## Discovery: collect evidence first

| Boundary | Required answer | Evidence |
| --- | --- | --- |
| Host | What is the non-interactive entry? Who owns exit? | CLI help, main entry, lifecycle tests |
| Carrier | Which protocol connects UI? What proves health? | Server config, routes, WebSocket/RPC definitions |
| Client | Does official UI run in a browser? Where are extensions? | Build output, Client manifest, slot/service APIs |
| Profile | Who owns config, plugins, sessions, and data roots? | Manifest, settings, home-path rules |
| Native | Which capabilities actually require OS adaptation? | Window, tray, terminal, update, file-picker needs |
| Packaging | Which runtimes, managers, and native modules ship? | Lockfile, ABI, libraries, release scripts |

## Pattern selection

```text
Is there an official local Web carrier?
├─ Yes: thin host; reuse Host, Carrier, and Client
└─ No
   ├─ Stable local server from CLI: sidecar
   ├─ Static Web UI only: static Client with remote API
   └─ TUI/private protocol only: define transport or Client first
```

## Minimal compatibility prototype

1. Pin upstream version and ownership; keep adapter branches out of upstream.
2. Start the official entry on random loopback and await explicit health.
3. Load a sandboxed window; keep navigation same-origin and externalize links.
4. Reuse the official Client, configuration, plugins, and data roots.
5. Dispose the Host or sidecar before allowing native process exit.
6. Verify Host, carrier root, and Client manifest with a headless smoke.

## Public contract decision

Only capabilities required by third-party plugins become public services. Keep
windows, tray, executable paths, ABI helpers, and installer paths internal.
Define public contracts by generation with cancellation, failure, and restart
semantics.

## Runtime closure

- Does the app ship the required Node, Python, Java, or target executable?
- Does it need pnpm, npm, or pip without changing the global PATH?
- Do native modules match runtime ABI, architecture, and platform?
- Can child processes resolve entries from ASAR or another virtual filesystem?
- May every bundled dependency be redistributed with its required notices?

## Release gates

| Gate | Passing condition |
| --- | --- |
| Ownership | Upstream pin, runtime family, and desktop ownership are verifiable |
| Loader/Host | Complete composition boots and audits without a GUI |
| Carrier | Loopback root, health signal, and Client manifest are automated |
| Lifecycle | Switching, failure, cancellation, and exit leak no handles |
| Package closure | Artifact contains all entries, native files, and licenses |
| Platform smoke | Target OS verifies native surfaces and installer behavior |

See the [lesson](../lessons/0001-harness-to-desktop.en.md) and the
[`harness-desktop-adapter` Skill](../skills/harness-desktop-adapter/SKILL.md).
