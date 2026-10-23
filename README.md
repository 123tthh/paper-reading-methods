# 论文精读方法 · Paper Reading Methods

**适用于不同 AI Agent 的论文精读技能与笔记模板。** 从研究问题出发，沿架构图拆解模块，解释关键公式，再把训练、推理与实验证据连起来。默认中文，支持按要求切换语言。

> An agent-independent skill for close reading of research papers: problem → mechanism → evidence. Includes reusable Markdown and HTML/CSS templates. No account, MCP server, API key, or model-specific runtime is required for reading the materials.

## 快速开始：任何能读文件的 Agent

下载本仓库，或克隆：

```bash
git clone https://github.com/123tthh/paper-reading-methods.git
cd paper-reading-methods
```

把下面的要求发给 Agent，并提供目标论文：

```text
请先读取 skills/paper-reading-methods/SKILL.md，并按其中的相对路径读取
references/method-guide.md 和 references/format-guide.md。
用这套方法精读我提供的论文，按“研究背景—方法论—实验”组织笔记，
解释模块、公式、训练与推理流程，并为结论标注原文证据。
未读到的内容明确标为未核实。请输出中文 HTML 笔记并检查渲染。
```

如果 Agent 不能访问本地文件，将上述三个 Markdown 文件连同目标论文作为附件提供；没有附件功能时按顺序粘贴其内容。需要视觉输出时同时提供 HTML 与 CSS 模板。只给一个 GitHub 链接不保证 Agent 会读取所有文件。

## 支持技能目录的 Agent

核心目录采用 [Agent Skills 格式](https://agentskills.io/specification)，可以整体复制 `skills/paper-reading-methods/` 到目标 Agent 官方文档指定的技能目录。必须保留 `references/` 和 `assets/`，不能只复制 `SKILL.md`。

**Claude Code（本地项目）**：在目标项目根目录创建 `.claude/skills/`，把完整的 `paper-reading-methods/` 技能目录复制进去，形成 `.claude/skills/paper-reading-methods/SKILL.md`；在该项目会话中输入 `/paper-reading-methods` 或直接提出精读请求。目录及调用方式依据 [Claude Code 官方文档](https://code.claude.com/docs/en/skills)。不要覆盖已有同名技能，先比较差异。

**Codex**：保留 `.codex-plugin/plugin.json` 与技能的 `agents/openai.yaml` 作为可选适配信息。支持本地插件的宿主可使用仓库根目录；仅支持技能目录的宿主使用完整技能目录，具体安装入口以该宿主版本为准。也可以使用上面的手动读取方式。

**Cursor、Gemini CLI、其他 Agent 或聊天模型**：可使用手动读取/附件方式；原生技能安装路径因产品和版本而异，参见 [兼容与能力说明](docs/compatibility.md)。本仓库不承诺未经实测的原生自动加载。

## 精读与排版规则

完整笔记保留三个正文一级章节：**1. 研究背景 → 2. 方法论 → 3. 实验**。摘要和来源放前面，结论与局限并入第三部分末尾；短问题直接短答，二级章节按论文实际内容调整。

- 背景：已有能力、具体困难和设计回应。
- 方法：总体接口、模块数据流、变量与公式、训练和推理全流程。
- 实验：主张、设置与对照、结果、原文出处和结论边界。
- 样式：蓝色编号与深色标题、浅灰加粗表头、正文等宽表格、变量居中与定义列表、绿色摘要/红色重点/紫色概念/橙色导读、公式独立居中。

HTML 模板可离线打开，样例公式使用 MathML 并保留 LaTeX 源码；它不是任意 LaTeX 的自动转换器。纯 Markdown 保留内容结构，无法保证字体、颜色、表格宽度或垂直对齐。

## 文件入口

| 文件 | 用途 |
|---|---|
| [SKILL.md](skills/paper-reading-methods/SKILL.md) | Agent 的核心执行说明 |
| [方法手册](skills/paper-reading-methods/references/method-guide.md) | 背景、模块、公式、流程与证据的讲解方法 |
| [格式规范](skills/paper-reading-methods/references/format-guide.md) | 标题、表格、说明块、图片和公式 |
| [HTML 模板](skills/paper-reading-methods/assets/paper-note-template.html) · [CSS](skills/paper-reading-methods/assets/paper-note-style.css) | 下载后放在同一目录，浏览器打开 HTML |
| [Markdown 模板](skills/paper-reading-methods/assets/paper-note-template.md) | 结构骨架 |
| [提示词示例](examples/prompts.md) | 完整精读、公式追问和笔记修订 |
| [飞书适配](skills/paper-reading-methods/references/feishu-formatting.md) | 可选的富文本操作与验收说明 |
| [来源与公开范围](skills/paper-reading-methods/references/source-map.md) | 方法来源、补充约定和授权边界 |

## 版本与验证

版本 **0.2.0**：将原有本地插件整理为平台无关的技能包，去除私人知识库依赖与会话记录，保留可选宿主配置。发布前检查文件引用、JSON 配置、技能元数据和公开内容。未在所有 Agent 中逐一运行，不将格式兼容视为端到端验证。阅读方法不需要外部服务；读取网络论文、PDF、编辑云端文档和渲染复杂公式取决于宿主能力。

## License

[MIT](LICENSE)。可使用、修改与分发本仓库的方法说明、模板和配置，遵守许可证中的署名与许可保留要求。外部论文和第三方材料不在本仓库授权范围内。


### 行内数学与方法论讲解规范

物理量、变量和带单位数值在正文、表格、图注及色块中均使用 LaTeX 并实际渲染；独立公式居中，行内公式随句排版。方法论按理解断点分布红色重点讲解块、紫色概念解释块，覆盖预备知识、关键机制和训练/部署衔接。模板和验收清单已同步。
