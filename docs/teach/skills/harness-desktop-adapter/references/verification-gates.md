# Verification gates

## Source and ownership

- Upstream revision and runtime package family are explicit.
- The upstream working tree is unchanged.
- Desktop-owned packages do not resolve production code through source-workspace links.

## Host and carrier

- A headless smoke reaches the authoritative boot-complete signal.
- The carrier binds only to the intended interface and selects its port safely.
- The root document and Client/module manifest load from the packaged dependency graph.
- Teardown disposes services and the full subprocess tree.

## Client security

- Renderer sandbox and context isolation are enabled.
- Node integration is disabled.
- In-app navigation remains on the exact allowed origin.
- External links use the operating system handler.
- Native operations cross narrow routes or services with origin and input validation.

## Profile and recovery

- Discovery is read-only.
- Selection persists before restart and commits healthy state only after mount.
- Failed pending state rolls back once to a last-known-good target.
- Service and process handles fail or dispose after their generation ends.

## Runtime closure

- Every production dependency and entry is present in the artifact.
- Native modules match target architecture and runtime ABI.
- Helpers that cannot execute from a virtual archive are physically unpacked.
- The artifact does not require a global runtime or package manager.
- Required licenses and notices are present.

## Platform smoke

- Window, tray, close-versus-quit, file picker, terminal, updater, and installer behavior are tested on each supported OS where applicable.
- GUI tests remain separate from the default headless gate.
- Signing and notarization claims are made only after verifying signed artifacts.
