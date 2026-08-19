# Carrier patterns

## Thin host over an existing Web carrier

Choose this when the target already owns a local Host, Web server, official browser Client, and stable lifecycle. Run the Host in the desktop process only when its runtime and failure behavior are compatible with that ownership; otherwise use a sidecar while preserving the same carrier.

Primary proof: the official Client loads from loopback and preserves plugins, settings, sessions, and storage without a Desktop-specific fork.

## Managed sidecar server

Choose this when the target exposes a stable server through a CLI or executable but cannot safely run inside the desktop process. The adapter owns exact argv, environment, stdout/stderr capture, readiness, cancellation, process-tree teardown, and restart recovery.

Primary proof: killing or restarting the desktop cannot leak the sidecar or its descendants.

## Packaged static Client over a remote API

Choose this when the product is a browser SPA backed only by a remote service. Package the existing build output and focus on authentication, CSP, CORS, deep links, offline states, update policy, and remote-service compatibility.

Primary proof: production authentication and API calls work from the packaged origin without weakening renderer security.

## Transport or Client prerequisite

Choose this when the target only provides a TUI, private in-memory API, undocumented stdout text, or native UI. Record the missing stable surface before estimating a desktop adapter. The next project is a public transport or Client, not an Electron wrapper.

Primary proof: the target project accepts or documents the new contract independently of the desktop shell.
