# 网站登录凭证管理

> 让 Agent 以你的身份登录网站，完成操作

## 用例场景

- **本地开发调试**：让 Agent 能完成登录态操作，测试不同用户的界面展示
- **保存平台登录凭证**：如 Reddit，定期获取论坛讨论信息
- **自动化内容发布**：如保存小红书登录凭证，自动发布内容

## 核心 Skill

| 类型 | 名称 | 来源 |
|------|------|------|
| Skill | playwright-auth-manager | [GitHub](https://github.com/kanlac/agile-dev) |

## 评分

| 维度 | 分数 | 说明 |
|------|------|------|
| 效果 | 5 | 完美解决登录态问题 |
| 复现成本 | 4 | 需运行 setup 脚本安装 Playwright |
| 稳定性 | 4 | 依赖 Playwright MCP，偶有环境问题 |
| 速度 | 5 | 一次登录，永久使用 |
| 可扩展性 | 4 | 支持多账号配置 |
| 兼容性 | 4 | Claude Code / OpenCode / Codex 均可用 |

**综合评分：4.2/5**

## 痛点解决

做本地开发时，你有没有遇到过：

- 需要测试不同用户看到的界面是否正确
- 需要检查不同权限用户的展示效果
- 需要验证多账号场景下的数据隔离

然后开始了循环：登出 → 登录账号 A → 测试 → 登出 → 登录账号 B → 再测试……

有些网站登录流程还特别复杂，两步验证、验证码，切换一次账号就要折腾好几分钟。

**Coding Agent 的困境**：它打开浏览器看到的是登录页面，不知道你的账号密码，也不能像你一样「记住」登录状态。

## 工作原理

你手动登录一次，脚本把登录信息（cookies + localStorage）保存到 JSON 文件，Agent 帮你配置好 MCP 自动加载。

**Skill 包含的脚本：**

| 脚本 | 功能 |
|------|------|
| setup.js | 环境准备，在 Skill 目录内安装 Playwright（不污染项目） |
| save-auth-state.js | 打开浏览器让你登录，按 Enter 后保存认证信息 |

## 使用示例

### 场景一：本地开发网站测试

**保存认证：**
```
你：我想保存本地开发网站 localhost:3000 的登录信息

Agent：好的，请在终端运行以下命令：
    node <path>/save-auth-state.js --url http://localhost:3000 --user dev-account

    运行后：
    1. 浏览器会自动打开
    2. 手动登录你的账号
    3. 登录完成后回到终端按 Enter
```

**使用登录态：**
```
你：用刚才保存的账号，帮我发一个测试帖子

Agent：好的，我会使用账号的认证状态。
    （Agent 自动处于登录状态，直接执行操作）
```

### 场景二：多账号测试

保存两份认证，配置两个 MCP 实例：

```
开发付费商品发布功能，用账号 A 发布一份付费产品，
然后用账号 B 登录网站检查展示效果
```

Agent 无缝切换，自动帮你调试、改 bug。

### 场景三：获取平台信息

登录 Reddit 等平台，定期抓取论坛讨论信息。

## 如何安装

在 Claude Code / OpenCode / Codex 中输入：

```
安装这个 skill https://raw.githubusercontent.com/kanlac/agile-dev/refs/heads/main/skill-install-guide.md
```

安装后直接说需求，如「我想保存小红书 xiaohongshu.com 的登录信息」，Agent 会自动加载 Skill 并指导操作。

## 高级用法

- 自动做社交矩阵
- 每天定时抓取整理实时资讯输出 JSON

注意小心被平台封号。

## 安全说明

- 脚本会自动检查 .gitignore，防止认证文件提交到代码仓库
- 认证文件很小（5-50KB），仅保存在本地

## 在 OpenCode 中使用

OpenCode 是开源的 Coding Agent 客户端，支持 Claude Code 的大部分功能：Skills, Subagents, Hooks, Slash Commands 等。

**使用 Codex/Gemini 订阅：**
```bash
opencode auth login
```

这个命令会启动 ChatGPT 登录流程，完成后就能在 OpenCode 中使用 Codex 订阅。

## 当前局限

虽然主流 Agent 工具都已支持 Agent Skills，但分发方式尚未完善：

- 需要为不同客户端写 MCP 配置手册
- 无法实现 Skills 自动更新（目前只有 Claude Code GitHub Marketplace 支持）

期待未来协议更新补上这块空缺。
