# 前端网页设计

> 用 Skill 做出审美在线、不 AI 味儿的网页

## 用例场景

- 快速生成活动页、落地页
- 设计产品原型、MVP 界面
- 制作个人作品集、博客页面

## 核心 Skill

| 类型 | 名称 | 来源 |
|------|------|------|
| Skill | frontend-design | [Anthropic 官方](https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md) |

## 评分

| 维度 | 分数 | 说明 |
|------|------|------|
| 效果 | 4.5 | 效果惊艳，偶有尾部排版小瑕疵 |
| 复现成本 | 5 | 安装即用，无需额外配置 |
| 通用性 | 4 | 每个团队可能有自己的设计风格，需微调 |
| 兼容性 | 4 | Claude Code / OpenCode / Codex 均可用 |

**综合评分：4.4/5**

## 效果对比

### 测试一：平安夜拆礼物页面

**Prompt:**
```
设计一个平安夜祝福的前端页面，要求可以交互（拆礼物），自适应移动端
```

#### Claude 直出（无 Skill）

![Claude 直出效果](./img/001/christmas-without-skill-1.jpg)

- 粗糙的展示
- Emoji 滥用，浓烈的 AI 味儿
- 字体用的是常规 Arial，毫无特色

#### 使用 frontend-design Skill

![使用 Skill 效果](./img/001/christmas-with-skill-1.jpg)

- 星空背景更有夜晚的感觉
- 雪花缓慢飘落并逐渐消失，细节拉满
- 选用 Cormorant Garamond 优雅字体，气氛浪漫

**高下立判。**

### 测试二：Skill Showcases 网站首页

**Prompt:**
```
创建一个「Skill Showcases」网站首页，网站主要内容为期刊形式发表的 skill 评测，
每期展示一个用例及其用到的 skill。希望有些有趣的交互增加互动感。
```

#### Claude 直出

![Claude 直出网站](./img/001/website-without-skill-1.jpg)

- 主题色是 AI 最爱的紫色
- 光标移动时有魔法粉末效果，像大学生博客
- 整体粗糙生硬

#### 使用 Skill

![使用 Skill 网站](./img/001/website-with-skill-1.jpg)

- 美学十分在线
- 标题和卡片的淡出效果恰到好处
- 按钮 hover 散发高级光晕
- 字体采用 Fraunces 衬线字体

**太惊艳了！远超初级前端工程师的水平，关键只用两句话几分钟内做出来的。**

#### Lovable（Figma Make 竞品）

![Lovable 效果](./img/001/lovable-website-1.jpg)

- 交互水平 80 分以上
- 标题用 Playfair Display，正文用 Inter（正是 Skill 中明确避免的常见字体）
- 有两下子，但没有 Skill 效果惊艳

## 原理拆解

frontend-design 除了强调美学（aesthetic）、创意等关键词外，还沉淀了 Anthropic 官方《前端美学：提示词指南》中的最佳实践。

**为什么 AI 不能「自动」展现美学能力？**

1. **Token 成本**：模型厂商不可能无限展开用户请求中的每个关键词
2. **意图含混不清**：当用户说「好看」「精美」时，描述的是模糊的感觉，含义需要澄清

好的 Skill 就应该这样——不需要华丽的提示词技巧，不需要反复润色，用户应该**毫无心智负担**地完成任务。

## 如何使用

安装 Skill 后，直接提出需求，Claude 会自动加载。建议尽可能描述清楚需求，包括用途、受众和技术限制等背景信息。

**一般提示词：**
```
帮我设计一个卖运动鞋的手机端商品卡片
```

**更好的提示词：**
```
请设计一个用于「限量版球鞋抽签发售」APP 的移动端商品卡片。
受众是追求潮流的 Z 世代用户，他们通常在几秒钟内做出购买决策，
因此视觉重心必须是高清的大尺寸鞋子图片和倒计时组件，弱化文字描述。
```

## 边界与局限

- 主要侧重 UI 设计，适合原型打磨
- **不要让它做复杂业务逻辑**
- 状态管理或复杂逻辑建议使用具体技术栈的 Skill

## 可选搭配

| 类型 | 名称 | 用途 | 来源 |
|------|------|------|------|
| Skill | webapp-testing | 确保页面功能可用无异常 | [GitHub](https://github.com/anthropics/skills/blob/main/skills/webapp-testing/SKILL.md) |
| Hook | learning-output-style | 跟随 agent 学习前端构建 | [GitHub](https://github.com/anthropics/claude-code/blob/main/plugins/learning-output-style/README.md) |
| Agent | code-architect | 后续的开发实现 | [GitHub](https://github.com/anthropics/claude-code/blob/main/plugins/feature-dev/agents/code-architect.md) |
