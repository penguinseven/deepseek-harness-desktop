# Harness Desktop Integration Resources

[English](RESOURCES.en.md)

## Knowledge

- [DSH Desktop 架构](../architecture.md)
  当前实现的一手总览。用于理解 Electron main、Cordis Host、loopback carrier、Web renderer 和 generation 生命周期。
- [为什么做 DSH Desktop](../why-desktop.md)
  产品边界说明。用于判断哪些能力应该复用上游，哪些能力属于桌面产品入口。
- [DSH Desktop package README](../../dsh-plugin-desktop/README.md)
  最完整的实现与发布说明。用于核对 profile 组合、运行环境、窗口安全和打包闭包。
- [Desktop 插件开发](../plugin-development.md)
  插件作者入口。用于区分普通 DSH contract、Desktop 公共 service 和内部 Electron capability。
- [Desktop plugin services](../../dsh-plugin-desktop/docs/plugin-services.md)
  `desktopProfiles` 与 `desktopPnpm` 的正式 contract。用于学习公共适配面和 generation-scoped 生命周期。
- [Pinned upstream and isolated Yarn workspace](../../.agents/notes/implemented/process/2026-08-15-pinned-upstream-and-isolated-yarn-workspace.md)
  源码所有权和包管理器边界决策。用于设计不修改上游的产品仓库结构。

## Wisdom (Communities)

- [DeepSeek Harness upstream issues](https://github.com/deepseek-ai/deepseek-harness/issues)
  用于确认上游真实行为、限制和扩展点，而不是从桌面适配层反推上游意图。
- [DSH Desktop product issues](https://github.com/penguinseven/deepseek-harness-desktop/issues)
  用于记录新目标 Harness 的接入调查、原型证据和平台验证结果。

## Gaps

- Qianwen Harness 或其他候选项目发布后，需要补充其官方启动、插件、Web transport、配置和发布文档。
- 纯远程 Web UI、带本地 sidecar 的 UI 与可组合 Host 的对比案例还需要更多真实项目验证。
