# Harness Desktop Adapter 速查表

[English](harness-desktop-adapter.en.md)

用 30 分钟判断一个新 Harness 或 Web UI 是否适合快速桌面化，并确定最小适配面。

## Discovery：先找证据

| 边界 | 必须回答 | 证据 |
| --- | --- | --- |
| Host | 非交互启动入口是什么？谁拥有进程和退出？ | CLI help、main entry、生命周期测试 |
| Carrier | UI 通过什么协议连接？端口和健康信号是什么？ | Server config、routes、WebSocket/RPC 定义 |
| Client | 官方 UI 能否在普通浏览器运行？扩展点在哪里？ | 构建输出、Client manifest、slot/service API |
| Profile | 配置、插件、会话和数据根由谁决定？ | Manifest、settings、home-path 规则 |
| Native | 哪些能力确实需要操作系统适配？ | 窗口、托盘、终端、更新、文件选择需求 |
| Packaging | 需要哪些解释器、包管理器和 native module？ | Lockfile、ABI、动态库、发布脚本 |

## 模式选择

```text
有官方本地 Web carrier？
├─ 是：薄宿主，复用 Host、Carrier 和 Client
└─ 否
   ├─ CLI 能启动稳定本地服务：Sidecar
   ├─ 只有静态 Web UI：静态 Client 与远程 API
   └─ 只有 TUI/私有协议：先设计稳定 transport 或 Client
```

## 最小兼容原型

1. 固定上游版本和所有权边界，不在适配分支修改上游源码。
2. 启动官方入口，使用随机 loopback 端口并等待明确健康信号。
3. 创建 sandboxed window，只允许同源导航，外部链接交给系统。
4. 复用官方 Client、配置、插件和数据目录。
5. 关闭时先 dispose Host/sidecar，再允许 native process 退出。
6. 用 headless smoke 验证 Host、carrier root 和 Client manifest。

## 公共 contract 判断

只有第三方插件确实需要的能力才成为公共 service。窗口、托盘、Electron executable、ABI helper 和安装器路径保持内部。公共 contract 按 generation 定义生命周期，并提供取消、失败和重启语义。

## 运行时闭包

- 解释器：Node、Python、Java 或目标二进制是否随应用提供？
- 包管理器：是否需要 pnpm、npm 或 pip，以及是否修改系统 PATH？
- Native ABI：Electron/Node ABI、架构和平台文件是否匹配？
- 物理路径：ASAR 或虚拟文件系统中的入口能否被子进程解析？
- 许可证：所有打包依赖是否允许再分发并包含 notice？

## 发布门禁

| 门禁 | 通过标准 |
| --- | --- |
| Ownership | 上游 pin、runtime package family 和桌面代码边界可验证 |
| Loader/Host | 不打开 GUI 也能启动并审计完整组合 |
| Carrier | Loopback root、健康信号和 Client manifest 可自动检查 |
| Lifecycle | 切换、失败、取消和退出不泄漏窗口、service 或进程树 |
| Package closure | 安装包包含所有运行入口、native 文件和许可证 |
| Platform smoke | 目标系统验证窗口、托盘、文件选择、终端和安装器 |

配套课程见[从 Harness 到 Desktop](../lessons/0001-harness-to-desktop.md)，参考 Skill 见 [`harness-desktop-adapter`](../skills/harness-desktop-adapter/SKILL.md)。
