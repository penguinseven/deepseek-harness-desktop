---
name: harness-desktop-adapter
description: Design or implement a compatibility-first desktop adapter for an agent harness, CLI-backed local web app, or standalone Web UI. Use when a user wants to desktopize, wrap, embed, package, or rapidly integrate a new Harness such as Qianwen Harness into Electron or Tauri, or when they need an evidence-backed assessment of whether an existing UI can be reused without forking upstream.
---

# Harness Desktop Adapter

Turn an existing Harness or Web UI into a desktop product by preserving its authoritative runtime and adding the smallest native adapter that closes the product lifecycle.

## Inputs

Establish these inputs from the request and repository before designing:

- target source or package and its authoritative version;
- desired desktop platforms;
- whether the task is assessment, prototype, implementation, or release hardening;
- required native capabilities such as tray, terminal, file picker, updater, or notifications.

If the target is not locally available and no authoritative documentation is reachable, produce a discovery-gap report. A speculative scaffold is not an integration result.

## 1. Protect ownership

Read repository instructions, Git status, remotes, submodules, package-manager files, and architecture decisions. Identify which trees are upstream-owned and which package owns desktop behavior. Preserve user changes and keep upstream source read-only when the repository defines that boundary.

Completion criterion: every source tree and generated artifact in scope has an owner, and the proposed work does not silently turn upstream code into desktop-owned code.

## 2. Build the evidence map

Read [references/discovery-checklist.md](references/discovery-checklist.md). Find concrete files or commands for all five layers:

1. **Host**: agent/runtime entry, service graph, process lifecycle.
2. **Carrier**: HTTP, WebSocket, RPC, stdio, or remote API boundary.
3. **Client**: official UI entry, build output, module or extension graph.
4. **Profile**: config, plugin composition, storage, sessions, credentials.
5. **Native**: capabilities that truly require an operating-system adapter.

Record unknowns beside the evidence. Do not infer a stable contract from private fields, incidental argv, undocumented URLs, or one successful manual launch.

Completion criterion: each layer has at least one authoritative evidence reference or is explicitly marked absent or unknown.

## 3. Select the carrier pattern

Read [references/patterns.md](references/patterns.md) and choose exactly one primary pattern:

- thin host over an existing local Web carrier;
- managed sidecar server;
- packaged static Client over a remote API;
- transport/client prerequisite when no stable embeddable surface exists.

Prefer the target's existing framework and transport. Choose Electron or Tauri only after the runtime and native-module requirements are known.

Completion criterion: the selected pattern explains how the UI starts, connects, becomes healthy, fails, and shuts down.

## 4. Write the integration contract

Define ownership and behavior for:

- upstream version pin and update procedure;
- Host or sidecar startup and shutdown;
- carrier origin, port selection, health signal, and navigation policy;
- Client reuse and extension discovery;
- profile/config/data identity;
- native internal adapter and any public plugin services;
- runtime closure, native ABI, licenses, and physical file paths;
- crash recovery and last-known-good behavior.

Expose a public Desktop service only when third-party code needs a stable capability. Keep window objects, tray registries, executable paths, ABI helpers, preload details, and installer internals private.

Completion criterion: every cross-layer call has one owner, one documented contract, and an explicit lifetime.

## 5. Build the compatibility tracer

For implementation requests, create the smallest end-to-end path:

1. acquire the native single-instance boundary when the product requires it;
2. launch the authoritative Host or sidecar without rewriting its domain behavior;
3. bind or discover a loopback carrier and wait for an explicit health signal;
4. load the official Client in a sandboxed window with no Node integration;
5. restrict in-app navigation to the expected origin and hand external links to the OS;
6. dispose the Host/service graph or complete subprocess tree before native exit;
7. verify the path headlessly before adding presentation work.

Use compatibility presentation first. Advanced frames, custom layouts, native materials, and replaced UI slots begin only after the tracer passes.

Completion criterion: one automated smoke proves authoritative runtime startup, carrier availability, Client discovery, and orderly teardown.

## 6. Add native capabilities through adapters

Add only capabilities named by the product requirements. Keep each adapter lifecycle-scoped and test it without opening the full GUI when possible. Provide cancellation and failure semantics for terminals, package operations, downloads, and child processes.

Prefer structured argv and exact executable entries over shell command strings. Keep bundled tools on a process-private PATH rather than modifying the user's global environment.

Completion criterion: every native capability has an owner, disposer, failure path, and focused test.

## 7. Close the packaged runtime

Inventory interpreters, package managers, native modules, dynamic libraries, static assets, licenses, and helper executables. Verify virtual archive paths versus physically unpacked paths. Match architecture and runtime ABI on every target platform.

Completion criterion: the packaged artifact resolves every production entry without source-workspace links, global developer tools, or undeclared files.

## 8. Verify and report

Read [references/verification-gates.md](references/verification-gates.md). Run the smallest relevant checks after each step and the complete repository gate at the end when prerequisites are available. Keep graphical launch explicit.

Report using this structure:

```markdown
# Integration assessment
## Evidence map
## Selected carrier pattern
## Integration contract
## Implemented tracer or implementation plan
## Verification
## Risks and deferred work
```

State commands that could not run and the exact missing prerequisite. Distinguish a source-level proof, a packaged-runtime proof, and a target-platform smoke.

## Guardrails

- Preserve the upstream Client and domain semantics in compatibility mode.
- Use loopback-only binding for local carriers unless remote access is an explicit product requirement.
- Keep renderer sandboxing and context isolation enabled.
- Treat profile and service references as generation-scoped when switching requires restart.
- Keep builds, type checks, unit tests, and Loader/Host smokes headless-safe.
- Separate upstream pin updates from desktop behavior changes so provenance remains reviewable.
