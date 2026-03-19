# stitch-design

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) custom skill for automating high-fidelity UI prototyping with [Google Stitch](https://stitch.withgoogle.com/) via MCP.

[Claude Code](https://docs.anthropic.com/en/docs/claude-code) 自定义技能，通过 MCP 自动化调用 [Google Stitch](https://stitch.withgoogle.com/) 生成高保真 UI 原型。

---

## What This Skill Does / 功能概述

When loaded by Claude Code, it turns Claude into a **Stitch prompt engineering expert** that can:

加载后，Claude 将成为 **Stitch 提示词工程专家**，具备以下能力：

- Generate high-fidelity UI screens from natural language descriptions
  从自然语言描述生成高保真 UI 界面
- Iteratively refine designs using battle-tested prompt patterns
  使用经过验证的 prompt 模式迭代优化设计
- Maintain visual consistency across multi-page apps
  跨多页面保持视觉一致性
- Control images, fonts, borders, and themes with precision
  精确控制图像、字体、边框和主题
- Auto-enhance vague ideas into structured Stitch prompts
  将模糊想法自动增强为结构化 Stitch 提示词

---

## Knowledge Included / 知识来源

This skill distills knowledge from:

本技能整合了以下来源的知识：

- **Official Stitch team guidance** (Vincent Nallatamby, Rishabh Chauhan)
  Stitch 官方团队指导
- **Community battle-tested patterns** from the Google AI Developers Forum
  Google AI 开发者论坛的社区实战经验
- **Production workflow** for automated generate-evaluate-iterate loops
  自动化"生成-评估-迭代"生产级工作流

### Prompt Engineering Rules / 提示词工程规则

| Rule | Detail |
|------|--------|
| Broad first, detail later | Start with a high-level concept, then drill into per-screen details |
| Global style first | Define colors / fonts / vibe BEFORE specific elements |
| Single change per prompt | Each prompt modifies ONE dimension only |
| Visual precision | Use Hex codes, material adjectives |
| Plain text preferred | Official recommendation: natural language, NOT XML/JSON |
| Adjectives set the vibe | Words like `vibrant`, `minimalist` influence everything |
| Reference by name | Always specify page name + component name + position |

| 规则 | 说明 |
|------|------|
| 先宽后细 | 先用高层次概念探索方向，再逐屏深入细节 |
| 全局样式先行 | 在具体元素之前先定义颜色、字体、氛围 |
| 每次只改一个维度 | 每个 prompt 只修改一个方面 |
| 视觉精确 | 使用 Hex 色值、材质形容词 |
| 纯文本优先 | 官方建议使用自然语言，不要用 XML/JSON |
| 形容词定基调 | `vibrant`、`minimalist` 等词直接影响全局风格 |
| 按名称引用 | 始终指明页面名 + 组件名 + 位置 |

### Topics Covered / 涵盖主题

- Structured prompt template with examples / 结构化提示词模板与示例
- 5-step workflow: Analyze -> Generate -> Evaluate -> Iterate -> Deliver / 五步工作流
- Multi-page consistency & consistency patching / 多页面一致性与修补
- Design variant exploration / 设计变体探索
- Image control techniques (batch, targeted, theme-coordinated) / 图像控制技巧
- Font & border fine-grained control / 字体与边框精细控制
- Multi-language UI patching / 多语言 UI 翻译修补
- Prompt Enhancer pattern (AI-assisted prompt generation) / Prompt 增强器模式
- Community tips & known failure modes with workarounds / 社区技巧与已知问题

---

## Installation / 安装

### Option 1: Clone / 方式一：克隆

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/blockbloomer/claude-skill-stitch-design.git ~/.claude/skills/stitch-design
```

### Option 2: Manual Copy / 方式二：手动复制

Download `SKILL.md` and the `examples/` directory, then place them in:

下载 `SKILL.md` 和 `examples/` 目录，放到以下路径：

```
~/.claude/skills/stitch-design/
  SKILL.md
  examples/
    prompt-examples.md
```

---

## Prerequisites / 前置条件

This skill requires a **Stitch MCP Server** connection. Below are the setup steps.

本技能需要 **Stitch MCP Server** 连接，以下是配置步骤。

### Step 1: Get Stitch API Key / 获取 Stitch API Key

1. Visit [stitch.withgoogle.com](https://stitch.withgoogle.com/) and sign in with your Google account
   访问 [stitch.withgoogle.com](https://stitch.withgoogle.com/) 并用 Google 账号登录
2. Click your avatar -> **Stitch Settings** -> **API Keys**
   点击头像 -> **Stitch Settings** -> **API Keys**
3. Create a new key and copy it
   创建新 Key 并复制

### Step 2: Configure Claude Code MCP / 配置 Claude Code MCP

Add [stitch-mcp](https://www.npmjs.com/package/@_davideast/stitch-mcp) (maintained by Google DevRel) to your MCP configuration:

将 [stitch-mcp](https://www.npmjs.com/package/@_davideast/stitch-mcp)（Google DevRel 官方维护）添加到 MCP 配置：

**Option A: Via CLI / 命令行方式：**

```bash
claude mcp add stitch -e STITCH_API_KEY=your_api_key_here -- npx @_davideast/stitch-mcp proxy
```

**Option B: Via config file / 配置文件方式：**

Edit `~/.claude/settings.json` (or project-level `.mcp.json`):

编辑 `~/.claude/settings.json`（或项目级 `.mcp.json`）：

```json
{
  "mcpServers": {
    "stitch": {
      "command": "npx",
      "args": ["@_davideast/stitch-mcp", "proxy"],
      "env": {
        "STITCH_API_KEY": "<your_api_key_here>"
      }
    }
  }
}
```

> **Note / 注意**: Never commit your API key to version control. Use environment variables or a `.env` file.
> 不要把 API Key 提交到版本控制。请使用环境变量或 `.env` 文件。

### Step 3: Verify / 验证

Restart Claude Code and confirm these MCP tools are available:

重启 Claude Code，确认以下 MCP 工具可用：

- `generate_screen_from_text`
- `get_screen`
- `edit_screens`
- `generate_variants`
- `list_screens`

---

## File Structure / 文件结构

```
stitch-design/
  SKILL.md                    # Core skill instructions / 核心技能指令 (380 lines)
  examples/
    prompt-examples.md        # 6 real-world prompt templates / 6 个实战提示词模板
  README.md                   # This file / 本文件
  LICENSE                     # MIT License
```

---

## Usage / 使用方法

Once installed, Claude Code will automatically detect the skill. Invoke it by asking Claude to generate UI designs:

安装后 Claude Code 会自动检测该技能。直接让 Claude 生成 UI 设计即可：

```
> Generate a login page for a fitness app using Stitch
> Create a dark mode dashboard with glassmorphism cards
> Design 3 variants of a recipe detail page
```

Claude will follow the skill's workflow: analyze requirements, build a structured prompt, generate via Stitch MCP, evaluate, and iterate up to 3 rounds.

Claude 会按技能工作流执行：分析需求 -> 构造结构化 prompt -> 调用 Stitch MCP 生成 -> 评估 -> 最多迭代 3 轮。

---

## Contributing / 贡献

Issues and PRs welcome. Key areas for contribution:

欢迎提交 Issue 和 PR，重点贡献方向：

- Additional prompt examples for specific domains / 特定领域的 prompt 示例
- New community-discovered techniques / 社区新发现的技巧
- Failure mode documentation and workarounds / 失败模式与解决方案

---

## License / 许可证

MIT
