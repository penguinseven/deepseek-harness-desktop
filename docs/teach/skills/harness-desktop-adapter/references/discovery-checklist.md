# Discovery Checklist

Use repository evidence and official documentation. Capture file paths,
commands, and observed output for every answer.

## Repository and Ownership

- Which remote and revision are authoritative?
- Is upstream a submodule, package dependency, vendored tree, or editable
  workspace?
- Which package owns launcher, native adapters, tests, and release scripts?
- Which package manager and lockfile govern each boundary?

## Host

- What non-interactive entry starts the runtime?
- Is the runtime in-process or a subprocess?
- What indicates boot completion?
- How does graceful shutdown work?
- How are plugins and services composed and disposed?

## Carrier

- Is the protocol HTTP, WebSocket, RPC, stdio, or remote-only?
- Can it bind to `127.0.0.1` on an ephemeral port?
- What endpoint or event proves readiness?
- Does authentication assume browser cookies, tokens, or filesystem state?
- Which origins, redirects, and external links are valid?

## Client

- Does the official UI run in a standard browser?
- Is it served by the Host or emitted as static assets?
- How are Client plugins or modules discovered?
- Which layout, service, or slot extension points are public?
- Does the UI depend on browser capabilities missing in a desktop renderer?

## Profile and Persistence

- Where do settings, sessions, credentials, plugins, and caches live?
- Is there a named profile or workspace identity?
- Which command is authoritative for plugin installation and reconciliation?
- Can profile changes happen live, or do they require a new generation?
- What is the rollback target after a failed switch?

## Packaging

- Which runtime, package manager, and helper executables are required?
- Which native modules bind to Node, Electron, Python, Java, or OS ABI?
- Which files must remain physically unpacked?
- Which licenses and notices must ship?
- Which tests prove the packaged artifact rather than the source tree?
