# Mission: 可迁移的 Harness 桌面化接入

[English](MISSION.en.md)

## Why

把 DSH Desktop 已经验证过的接入经验提炼成可重复的方法，使团队面对 Qianwen Harness、其他 Agent Harness 或新的 Web UI 时，能够先识别边界，再快速交付兼容优先的桌面版本，而不是重新实现上游产品。

## Success looks like

- 能在阅读一个新项目后，画出 Host、Carrier、Client、Profile 和 Native 五层边界。
- 能根据证据选择薄宿主、sidecar、静态 UI 或外部浏览器等接入模式。
- 能完成一个不修改上游源码的兼容模式原型，并保留上游插件和数据语义。
- 能定义运行时闭包、安全边界、恢复策略和发布验证门禁。
- 能使用仓库中的 `harness-desktop-adapter` Skill 草案指导后续接入工作。

## Constraints

- 上游源码保持可追溯、可比较，桌面功能由独立拥有的代码承载。
- 兼容模式优先；高级外观只能建立在稳定载体和服务边界之上。
- 构建、类型检查、单元测试和 Loader smoke 保持 headless-safe。
- 教学材料使用中文，保留必要的英文架构术语和代码标识符。

## Out of scope

- 为尚未发布的目标 Harness 预写具体适配代码。
- 重做上游 Agent、模型、会话或插件语义。
- 代码签名、应用商店审核和生产证书运维。
