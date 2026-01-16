# Skills Radar

精选 Claude Skills 评测，帮你找到真正好用的 AI 技能。

## 为什么做这个

Skills 聚合的网站很多，但几乎没有哪个告诉你：
- 这个 Skill **怎么用**
- 实际效果**好不好**
- **替代方案**有哪些

我们以**用例（Use Case）**为单位撰写评测，而非 Skill 本身。因为 Skill 只是解决某个问题的工具，你真正关心的是：**这个场景下，什么方案最好用**。

## 评测标准

每个维度 0-5 分，详见 [评测标准说明](./RATING.md)

| 维度 | 说明 |
|------|------|
| 效果 | 是否真的解决问题（含稳定性） |
| 复现成本 | 安装/配置/依赖的复杂度 |
| 通用性 | 不需要定制化就能满足需求的程度 |
| 兼容性 | Claude Code / OpenCode / Codex 等客户端支持情况 |

## 评测文章

| 用例 | 核心 Skill | 综合评分 |
|------|-----------|---------|
| [前端网页设计](./usecases/frontend-design.md) | frontend-design | 4.4/5 |
| [电子表格处理](./usecases/xlsx.md) | xlsx | 4.3/5 |
| [网站登录凭证管理](./usecases/playwright-auth.md) | playwright-auth-manager | 4.4/5 |
| [设计封面](./usecases/canvas-design.md) | canvas-design | 3.5/5 |
| 公众号主题定制 | theme-factory | 待评测 |
| NotebookLM 集成 | [notebooklm-skill](https://mcpservers.org/claude-skills/pleaseprompto/notebooklm-skill) | 待评测 |
| Notion 官方 skills | [Notion Skills for Claude](https://www.notion.so/notiondevs/Notion-Skills-for-Claude-28da4445d27180c7af1df7d8615723d0) | 待评测 |
| AI 语音通话 | [call-me](https://github.com/ZeframLou/call-me) | 待评测 |
| 全栈开发工作流 | [superpowers](https://github.com/obra/superpowers) | 待评测 |
| 复利工程 | [compound-engineering](https://github.com/EveryInc/compound-engineering-plugin) | 待评测 |

## 如何安装 Skill

不同 Agent 工具安装 Skill 的方法有所不同：

### Claude Code

**方法一：GitHub Marketplace（推荐）**

访问 [Claude Code Plugins](https://github.com/anthropics/claude-code/tree/main/plugins)，找到需要的 Skill，点击安装。支持自动更新。

**方法二：手动安装**

将 Skill 文件（如 `SKILL.md`）放入项目的 `.claude/skills/` 目录：

```bash
mkdir -p .claude/skills
curl -o .claude/skills/SKILL.md <skill-url>
```

### OpenCode

OpenCode 完全兼容 Claude Code 的 Skill 格式。

**安装方式：**

直接告诉 Agent 安装链接：

```
安装这个 skill https://raw.githubusercontent.com/<repo>/SKILL.md
```

Agent 会自动下载并配置。

**使用 Codex/Gemini 订阅：**

```bash
opencode auth login
```

完成 ChatGPT 登录流程后即可使用 Codex 订阅。

### OpenAI Codex

Codex 通过内置的 `skill-installer` 安装 Skill：

```bash
$skill-installer https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md
```

**注意：** 网页端 Codex 和 ChatGPT 目前不支持 Skill。

### 通用方法

对于任何支持 Agent Skills 的客户端，都可以直接将 `SKILL.md` 文件放入项目目录，Agent 会自动识别并加载。

## 参与贡献

欢迎通过以下方式参与：

- **提名 Skill**：[提交 Issue](../../issues/new) 告诉我们你想看哪个 Skill 的评测
- **贡献评测**：Fork 本仓库，按照 [评测模板](./TEMPLATE.md) 撰写，提交 PR
- **纠错反馈**：发现评测有误？欢迎提 Issue 或 PR

## 关键词

Claude Skills, Agent Skills, AI Evaluation, Skill 评测, 精选推荐

## License

MIT
