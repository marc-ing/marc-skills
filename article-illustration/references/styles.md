# 配图风格、配色与预设

枚举值用于命令、配置和提示词元数据，保持英文。根据文章内容选择风格，不按个人偏好机械套用。

## 风格

| 标识 | 视觉特征 | 适用内容 |
|---|---|---|
| `sketch-notes` | 米白纸张、黑色手绘线、柔和色块 | 通用知识、教学、概念解释，默认 |
| `ink-notes` | 纯白背景、黑色墨线、少量语义强调色 | 前后对比、方法框架、技术观点 |
| `vector-illustration` | 清晰轮廓、几何形状、平涂色块 | 教程、产品、技术与知识内容 |
| `notion` | 极简黑白线稿、少量柔和强调色 | SaaS、效率工具、轻量说明 |
| `blueprint` | 蓝底或工程纸、网格、标注和结构线 | 架构、系统设计、工程原理 |
| `editorial` | 杂志信息图、清晰标题层级、数据化布局 | 数据报道、行业分析、评论 |
| `scientific` | 精确示意、规范标注、低装饰 | 科研、医学、技术研究 |
| `elegant` | 克制配色、精细线条、充足留白 | 商业、策略、思想内容 |
| `minimal` | 单一视觉焦点、大面积留白 | 核心观点、哲思、极简主题 |
| `warm` | 暖色、圆润形状、亲近人物与环境 | 成长、教育、团队和生活方式 |
| `watercolor` | 柔软边缘、水彩晕染、自然质感 | 旅行、生活、创意和情绪叙事 |
| `screen-print` | 粗线、网点、有限色、海报构图 | 评论、文化、戏剧性叙事 |
| `chalkboard` | 黑板、粉笔线和课堂图示 | 教学、解释、步骤说明 |
| `flat` | 大块几何色面、现代数字视觉 | 当代产品与互联网内容 |
| `flat-doodle` | 粗轮廓、可爱图形、轻松表情 | 轻知识、亲子和友好内容 |
| `fantasy-animation` | 原创手绘动画感、柔光、叙事环境 | 童话、情感和想象类故事 |
| `intuition-machine` | 旧纸、技术简报、机械标记 | 技术史、研究笔记和概念装置 |
| `nature` | 植物、有机曲线、土壤与自然材质 | 环境、健康、可持续和成长 |
| `pixel-art` | 像素网格、抖动色、8 位图形 | 游戏、复古科技和数字文化 |
| `playful` | 柔和涂鸦、跳跃形状、轻松节奏 | 趣味教学和休闲内容 |
| `retro` | 80/90 年代几何、霓虹和怀旧配色 | 复古科技、流行文化 |
| `sketch` | 铅笔草图、笔记本质感、不完美线条 | 头脑风暴、早期概念和创作过程 |
| `vintage` | 做旧纸张、传统纹样和历史色调 | 历史、传承与文化主题 |

避免直接模仿在世艺术家的个人风格，也不要要求复刻受保护角色。将风格描述为可观察的视觉特征。

## 配色

| 标识 | 配色特征 | 适用内容 |
|---|---|---|
| `macaron` | 米白背景，浅蓝、薄荷、薰衣草和桃色 | 教学、知识卡片和柔和手绘 |
| `warm` | 橙、陶土、金黄和柔桃色，避免冷色主导 | 品牌、产品、教育和生活方式 |
| `neon` | 深紫或近黑背景，粉、青、黄霓虹 | 游戏、未来感和流行文化 |
| `mono-ink` | 黑白为主，珊瑚红、灰蓝绿或淡紫少量强调 | 专业视觉笔记和对比框架 |
| `default` | 使用所选风格的自然配色 | 没有明确品牌或情绪要求时 |

配色用于建立层级，不得让每个元素都使用强调色。文本与背景必须保持足够对比。

## 类型与风格建议

| 类型 | 首选风格 | 可选风格 |
|---|---|---|
| `infographic` | `sketch-notes` | `vector-illustration`、`editorial`、`scientific` |
| `scene` | `warm` | `watercolor`、`screen-print`、`fantasy-animation` |
| `flowchart` | `vector-illustration` | `notion`、`blueprint`、`ink-notes` |
| `comparison` | `ink-notes` | `vector-illustration`、`elegant`、`screen-print` |
| `framework` | `blueprint` | `vector-illustration`、`ink-notes`、`scientific` |
| `timeline` | `elegant` | `warm`、`editorial`、`vintage` |

## 常用预设

| 预设 | 类型 | 风格 | 配色 | 适用内容 |
|---|---|---|---|---|
| `hand-drawn-edu` | `infographic` | `sketch-notes` | `macaron` | 通用教学和概念总览，默认 |
| `hand-drawn-edu-flow` | `flowchart` | `sketch-notes` | `macaron` | 步骤与流程解释 |
| `hand-drawn-edu-compare` | `comparison` | `sketch-notes` | `macaron` | 友好的并列比较 |
| `ink-notes-compare` | `comparison` | `ink-notes` | `mono-ink` | 前后变化、传统与新方法 |
| `ink-notes-flow` | `flowchart` | `ink-notes` | `mono-ink` | 专业流程和技术说明 |
| `ink-notes-framework` | `framework` | `ink-notes` | `mono-ink` | 系统类比与方法框架 |
| `tech-explainer` | `infographic` | `blueprint` | `default` | 技术原理和系统指标 |
| `system-design` | `framework` | `blueprint` | `default` | 架构和模块关系 |
| `science-paper` | `infographic` | `scientific` | `default` | 研究结果和实验说明 |
| `saas-guide` | `infographic` | `notion` | `default` | 产品指南和工具教程 |
| `data-report` | `infographic` | `editorial` | `default` | 数据分析和行业报告 |
| `business-compare` | `comparison` | `elegant` | `default` | 商业方案与策略选择 |
| `storytelling` | `scene` | `warm` | `default` | 个人故事和成长叙事 |
| `lifestyle` | `scene` | `watercolor` | `default` | 旅行、健康和生活方式 |
| `history` | `timeline` | `elegant` | `default` | 历史与里程碑 |
| `opinion-piece` | `scene` | `screen-print` | `default` | 评论与文化观察 |

## 自动选择

- 技术、API、架构、模块、网络：优先 `blueprint` 或 `vector-illustration`。
- 教程、步骤、概念解释、入门：优先 `hand-drawn-edu`。
- 数据、指标、趋势、市场：优先 `editorial`。
- 对比、转变、旧方法与新方法：优先 `ink-notes-compare`。
- 故事、经历、情绪、旅行：优先 `warm` 或 `watercolor`。
- 历史、阶段、版本演进：优先时间线和 `elegant`。
- 文章没有强烈视觉信号时，使用 `hand-drawn-edu`，不要随机选择夸张风格。
