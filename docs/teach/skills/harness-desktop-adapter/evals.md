# Harness Desktop Adapter Eval Prompts

## 1. Qianwen Harness with a local Web carrier

**Prompt:** Qianwen Harness has just been published in this repository. It
exposes `qwen web --port 0`, prints a localhost URL, stores sessions under a
named profile, and ships a React client. Assess the repository and implement
the smallest Windows/macOS desktop compatibility prototype without editing the
upstream checkout.

**Expected result:** An evidence-backed five-layer assessment, selection of the
thin-host or sidecar pattern from actual runtime constraints, a minimal
compatibility implementation, and headless verification of startup, carrier,
Client, and teardown.

## 2. Static Web UI with a hosted API

**Prompt:** We have an existing static XX Web UI that talks only to a hosted
API. Product wants an Electron app with auto-update and native file selection.
Determine what can be reused, what security boundaries are required, and
produce an implementation plan without inventing local profiles or a plugin
runtime.

**Expected result:** Selection of the packaged-static-Client pattern, explicit
authentication, CSP, CORS, and native-operation contracts, no copied
Harness-only profile concepts, and packaged-runtime plus platform verification
gates.

## 3. TUI-only agent tool

**Prompt:** This agent tool currently has only an interactive terminal UI and
emits human-readable logs. Leadership says to wrap it in Tauri this week.
Diagnose whether rapid desktop integration is actually possible and identify
the smallest prerequisite contract before estimating implementation.

**Expected result:** A discovery-gap report that rejects framework-first
scaffolding, identifies the missing stable transport or Client contract, and
defines observable acceptance criteria for that prerequisite.
