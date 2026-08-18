---
name: article-illustration
description: 分析 Markdown 文章的结构和论证，判断适合插图的位置，并按「类型 × 风格 × 配色」生成风格统一的位图插图。当用户要求“为文章配图”“添加插图”“生成文章图片”“把文章做成图文版”或希望用信息图、流程图、对比图、框架图、时间线和叙事场景辅助表达时使用。默认先确认配图方案，再保存大纲与完整提示词，生成图片并把相对路径写回原文。
---

# 文章配图

为文章选择真正需要视觉辅助的位置，生成内容准确、风格一致、可复现的位图插图。插图服务于理解，不负责重复正文或单纯装饰。

## 基本原则

- 不改写、删减或调整文章原文，只在确认的位置插入图片引用。
- 先理解论点、数据、流程和叙事关系，再决定是否配图。
- 抽象概念优先呈现其内在关系，不把比喻机械画成字面场景。
- 图中出现的数字、术语、引语和标签必须来自原文或用户确认的信息。
- 必须调用可用的位图生成工具，不得用 SVG、HTML、Canvas 或 CSS 绘图替代。
- 图中文字有误时重新生成。不得用 Pillow、ImageMagick、OCR、SVG 或其他程序覆盖、擦除或重写成图文字。
- 每张图生成前都要把完整最终提示词保存到文件，不能只向生成工具传递临时提示词。

## 用户交互

需要用户选择时，优先使用当前运行环境提供的交互式提问工具。没有此类工具时，使用编号问题让用户回复。能合并的问题一次提出，最多四个，避免来回追问。

默认在生成前确认方案。只有用户在当前请求中明确说“直接生成”“不用确认”“按默认出图”或同等意思时，才可跳过确认；跳过时应先说明采用的类型、密度、风格、配色、语言和生成后端。

## 图片生成后端

按以下顺序选择后端：

1. 用户在当前请求中指定的后端。
2. `EXTEND.md` 中的 `preferred_image_backend`，前提是当前环境可用。
3. 当前环境原生的位图生成能力。Codex 中如存在 `imagegen` Skill，先读取并遵守该 Skill，再调用对应工具。
4. 当前环境中唯一可用的其他位图生成工具。
5. 没有可用后端时停止生成，说明缺少能力并询问用户如何继续。

`preferred_image_backend: ask` 表示每次都询问。固定后端不可用时退回自动选择。

## 配图维度

### 类型

| 标识 | 适用内容 |
|---|---|
| `infographic` | 数据、指标、概念总览和技术说明 |
| `scene` | 故事、体验、情绪和生活方式内容 |
| `flowchart` | 步骤、流程、工作流和因果链 |
| `comparison` | 方案、阶段或观点的并列比较 |
| `framework` | 模型、系统、架构和层级关系 |
| `timeline` | 历史、演进、里程碑和阶段变化 |
| `mixed` | 同一文章中组合多种类型 |

### 密度

| 标识 | 数量参考 |
|---|---|
| `minimal` | 1–2 张，只保留最关键视觉 |
| `balanced` | 3–5 张，覆盖主要论点 |
| `per-section` | 每个确有视觉价值的章节一张，默认推荐 |
| `rich` | 6 张以上，适合长教程或强视觉内容 |

风格、配色和预设见 [references/styles.md](references/styles.md)。枚举值保持英文，解释和生成提示使用中文。

## 工作流程

### 第一步 读取输入和偏好

读取用户提供的 Markdown 文件或粘贴文本。文件模式保留原文件；粘贴模式先把内容保存为 `source-{slug}.md`。

按优先级查找首个存在的 `EXTEND.md`：

1. `.marc-skills/article-illustration/EXTEND.md`
2. `${XDG_CONFIG_HOME:-$HOME/.config}/marc-skills/article-illustration/EXTEND.md`
3. `$HOME/.marc-skills/article-illustration/EXTEND.md`

未找到时使用 [references/preferences.md](references/preferences.md) 中的默认值，不把首次配置设为阻塞步骤。用户明确要求保存偏好时，再创建配置文件。

### 第二步 处理参考图片

识别用户上传、粘贴或通过 `--ref` 指定的图片。复制到输出目录的 `references/` 中，并逐张判断用途：

- `direct`：主体、人物或构图需要直接参考，生成时传给支持参考图的后端。
- `style`：只提取线条、质感、构图和视觉语言。
- `palette`：只提取配色比例与色彩关系。

详细规则见 [references/workflow.md](references/workflow.md)。

### 第三步 分析文章并确认方案

提取内容类型、核心论点、关键数据、流程关系、叙事转折和适合插图的位置。没有信息增量的位置不要配图。

一次确认以下内容：

1. 推荐预设或配图类型。
2. 配图密度。
3. 风格；选择预设后可省略。
4. 配色；预设或偏好已确定时可省略。
5. 文章语言与偏好不一致时，再确认图中文字语言。

### 第四步 生成配图大纲

在输出目录保存 `outline.md`，记录类型、密度、风格、配色和图片数量。每张图至少写明：

```markdown
## 配图 1

**位置**：章节或段落
**目的**：为什么需要这张图
**视觉内容**：画面结构和信息
**文件名**：01-infographic-concept-name.png
```

### 第五步 保存提示词并生成图片

先按 [references/prompt-construction.md](references/prompt-construction.md) 为所有图片建立 `prompts/NN-{type}-{slug}.md`，检查提示词中包含布局、标签、颜色、风格、比例和禁用项，然后才可生成。

默认批量生成：优先使用后端批处理能力；其次使用当前运行环境支持的并行工具调用，每批默认最多 4 张；均不可用时串行生成。失败项只重试一次，不重复生成成功项，也不使用子 Agent 单纯并行出图。

### 第六步 写回文章并交付

把图片引用插入对应段落之后：

```markdown
![准确描述图片内容的替代文字](imgs/01-infographic-concept-name.png)
```

最后报告文章路径、采用的方案、成功图片数量、失败项和输出目录。

## 输出结构

默认写入文章同级的 `imgs/`：

```text
{output-dir}/
├── outline.md
├── prompts/
│   └── NN-{type}-{slug}.md
├── references/
│   └── NN-ref-{slug}.{ext}
└── NN-{type}-{slug}.png
```

`default_output_dir` 可取：

| 值 | 输出位置 |
|---|---|
| `imgs-subdir` | `{article-dir}/imgs/`，默认 |
| `same-dir` | `{article-dir}/` |
| `illustrations-subdir` | `{article-dir}/illustrations/` |
| `independent` | 当前目录下 `illustrations/{topic-slug}/` |

粘贴文本始终使用 `illustrations/{topic-slug}/`。`slug` 使用 2–4 个小写英文单词和连字符；同名时追加时间戳。

## 修改已有配图

- 修改：保留旧图，创建新提示词和新输出路径后重新生成，再更新文章引用。
- 新增：确认位置，更新大纲，保存提示词，生成并插入。
- 删除：删除图片引用并更新大纲；删除文件前确认目标准确。
- 仅允许裁剪、缩放、压缩和格式转换等不改变文字与主体构图的后处理。

## 参考文件

- [references/workflow.md](references/workflow.md)：输入、参考图、分析、批量生成和写回细则。
- [references/styles.md](references/styles.md)：类型、风格、配色、预设及自动选择。
- [references/prompt-construction.md](references/prompt-construction.md)：提示词文件格式和不同类型模板。
- [references/preferences.md](references/preferences.md)：`EXTEND.md` 配置格式。
- [prompts/system.md](prompts/system.md)：所有图片提示词共同遵守的视觉约束。
