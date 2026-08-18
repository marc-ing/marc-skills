---
name: article-cover-image
description: 根据文章主题和使用场景生成文章封面位图，通过构图类型、配色、绘制方式、文字密度、情绪强度和字体气质六个维度控制结果。当用户要求“生成文章封面”“制作博客头图”“做公众号封面”“创建横版或方形社交卡片”时使用。支持 2.35:1、16:9、4:3、3:2、1:1 和 3:4 等比例，默认先分析文章并确认方案，再保存完整提示词、生成封面并交付源文件。
---

# 文章封面图

为文章生成与内容相符、层级清晰、适配目标平台的位图封面。封面应传达主题和气质，不应把文章摘要塞进画面。

## 基本原则

- 先读文章或摘要，再决定视觉隐喻、构图和标题层级。
- 标题只能使用用户或原文中的准确文字，不自行改写或发明副标题。
- 不添加作者署名、品牌、网址、二维码、签名或水印，除非用户明确提供并要求使用。
- 必须使用位图生成工具，不得用 SVG、HTML、Canvas 或 CSS 绘图代替。
- 成图文字错误时重新生成，不得用程序覆盖、擦除或重写图片文字。
- 生成前必须把完整最终提示词保存到 `prompts/`。
- 用户提供的参考图片只用于其明确允许的主体、构图、风格或配色，不复制无关文字和标志。

## 用户交互

优先使用当前运行环境提供的交互式提问工具；没有时使用编号问题。一次最多提出四个问题，相关设置可合并。

默认在生成前确认方案。只有用户在当前请求中明确说 `--quick`、“直接生成”“不用确认”“按默认出图”或配置中设置 `quick_mode: true` 时，才可跳过确认。跳过时先说明选定的六个维度、比例、语言和生成后端。

## 图片生成后端

按以下顺序选择：

1. 用户当前请求指定的后端。
2. `EXTEND.md` 中可用的 `preferred_image_backend`。
3. 当前环境原生的位图生成能力。Codex 中如存在 `imagegen` Skill，先读取并遵守该 Skill，再调用对应工具。
4. 当前环境中唯一可用的其他位图生成工具。
5. 没有可用后端时停止，说明限制并询问用户。

`preferred_image_backend: ask` 表示每次询问。固定后端不可用时退回自动选择。

## 参数

| 参数 | 可选值 |
|---|---|
| `--type` | `hero`、`conceptual`、`typography`、`metaphor`、`scene`、`minimal` |
| `--palette` | `warm`、`elegant`、`cool`、`dark`、`earth`、`vivid`、`pastel`、`mono`、`retro`、`duotone`、`macaron` |
| `--rendering` | `flat-vector`、`hand-drawn`、`painterly`、`digital`、`pixel`、`chalk`、`screen-print` |
| `--style` | 风格预设，见 [references/options.md](references/options.md) |
| `--text` | `none`、`title-only`、`title-subtitle`、`text-rich` |
| `--mood` | `subtle`、`balanced`、`bold` |
| `--font` | `clean`、`handwritten`、`serif`、`display` |
| `--aspect` | `16:9`、`2.35:1`、`4:3`、`3:2`、`1:1`、`3:4` |
| `--lang` | `zh`、`en`、`ja` 等语言代码 |
| `--no-title` | 等同于 `--text none` |
| `--quick` | 跳过方案确认，使用自动选择 |
| `--ref` | 一个或多个参考图片路径 |

各维度含义、兼容关系和自动选择规则见 [references/options.md](references/options.md)。

## 工作流程

### 第零步 读取偏好

按顺序读取首个存在的 `EXTEND.md`：

1. `.marc-skills/article-cover-image/EXTEND.md`
2. `${XDG_CONFIG_HOME:-$HOME/.config}/marc-skills/article-cover-image/EXTEND.md`
3. `$HOME/.marc-skills/article-cover-image/EXTEND.md`

不存在时使用 [references/preferences.md](references/preferences.md) 中的默认值，不强制进行首次配置。

### 第一步 分析输入

1. 读取文章、摘要或用户说明；粘贴内容保存为 `source-{slug}.md`。
2. 提取主题、语气、关键词、核心冲突和可视化隐喻。
3. 识别标题原文和目标语言。
4. 保存并分析参考图片，规则见 [references/reference-images.md](references/reference-images.md)。
5. 根据目标平台确定比例和输出目录。

### 第二步 确认方案

一次确认以下内容，已由参数指定的项目不再询问：

1. 构图类型。
2. 配色。
3. 绘制方式。
4. 其他设置：文字密度、情绪、字体、比例和语言。

每项把推荐选项放在第一位并说明理由。只要仍有关键选择未确定，就不能进入生成步骤；用户明确使用快速模式时除外。

### 第三步 保存提示词

使用 [references/prompt-template.md](references/prompt-template.md) 创建 `prompts/01-cover-{slug}.md`。提示词必须包含内容语境、六个维度、准确文字、构图、比例、参考图用途和禁止项。

### 第四步 生成并检查

1. 已存在 `cover.png` 时先保留旧版本，使用新文件名生成候选。
2. 把提示词文件内容、输出路径、比例和 `direct` 参考图传给选定后端。
3. 失败时自动重试一次。
4. 检查文件可打开、比例正确、标题准确、主体清楚、没有多余文字和标志。
5. 有文字或构图问题时创建新提示词和新输出路径重新生成。

### 第五步 交付

报告主题、六个维度、比例、语言、参考图数量和输出路径。不要在回复中重复完整提示词。

## 输出结构

```text
{output-dir}/
├── source-{slug}.{ext}
├── references/
│   └── ref-01-{slug}.{ext}
├── prompts/
│   └── 01-cover-{slug}.md
└── cover.png
```

`default_output_dir` 可取：

| 值 | 输出位置 |
|---|---|
| `independent` | 当前目录下 `cover-image/{topic-slug}/`，默认 |
| `same-dir` | 文章所在目录 |
| `imgs-subdir` | 文章同级的 `imgs/` |

`slug` 使用 2–4 个小写英文单词和连字符；发生冲突时追加时间戳。

## 构图底线

- 保留足够呼吸空间，通常让 40%–60% 的画面保持简洁。
- 主视觉必须明确，可居中或偏置，但不能与标题争抢焦点。
- 标题与主体之间保持安全距离，移动端缩略图仍应可读。
- 人物优先使用简化、原创、不可识别的造型，除非用户合法提供特定人物参考。
- `minimal` 类型至少保留约 60% 留白；`typography` 类型让标题成为主要视觉元素。

## 修改封面

- 重新生成：保留旧图，先更新提示词文件，再生成新候选。
- 修改维度：确认新值，更新提示词后生成。
- 仅允许裁剪、缩放、压缩和格式转换等不改变文字与主体构图的后处理。

## 参考文件

- [references/options.md](references/options.md)：六个维度、预设、兼容关系和自动选择。
- [references/prompt-template.md](references/prompt-template.md)：完整提示词格式。
- [references/reference-images.md](references/reference-images.md)：参考图片保存和分析规则。
- [references/preferences.md](references/preferences.md)：`EXTEND.md` 配置格式。
