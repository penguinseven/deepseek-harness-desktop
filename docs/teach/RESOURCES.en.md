# Harness Desktop Integration Resources

[中文](RESOURCES.md)

## Knowledge

- [DSH Desktop architecture](../architecture.en.md)
  The primary implementation overview for Electron main, Cordis Host, the
  loopback carrier, Web renderer, and generation lifetime.
- [Why DSH Desktop](../why-desktop.en.md)
  Product-boundary rationale for deciding what belongs upstream and what
  belongs to the desktop entry point.
- [DSH Desktop package README](../../dsh-plugin-desktop/README.md)
  The detailed implementation and release reference for profiles, runtime
  environment, window security, and packaged runtime closure.
- [Desktop plugin development](../plugin-development.en.md)
  The boundary between ordinary DSH contracts, public Desktop services, and
  internal Electron capabilities.
- [Desktop plugin services](../../dsh-plugin-desktop/docs/plugin-services.md)
  The formal contracts for `desktopProfiles` and `desktopPnpm`.
- [Pinned upstream and isolated Yarn workspace](../../.agents/notes/implemented/process/2026-08-15-pinned-upstream-and-isolated-yarn-workspace.md)
  The source-ownership and package-manager boundary decision.

## Wisdom (Communities)

- [DeepSeek Harness upstream issues](https://github.com/deepseek-ai/deepseek-harness/issues)
  Use to confirm real upstream behavior, limitations, and extension points.
- [DSH Desktop product issues](https://github.com/penguinseven/deepseek-harness-desktop/issues)
  Use to record discovery, prototype evidence, and platform-verification
  results for a new target Harness.

## Gaps

- When Qianwen Harness or another target is published, add its official
  startup, plugin, Web transport, configuration, and release documentation.
- More real projects are needed to compare remote-only UIs, local sidecars, and
  composable Hosts.
