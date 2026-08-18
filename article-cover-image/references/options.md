# 封面设计选项

命令和配置中的枚举值保持英文。选择时先服从内容和平台，再考虑个人偏好。

## 构图类型

| 标识 | 构图特征 | 适用内容 |
|---|---|---|
| `hero` | 主视觉占约 60%–70%，标题叠放或并列 | 发布、品牌、重要公告 |
| `conceptual` | 用抽象形状和关系表达核心概念 | 技术、方法论、系统设计 |
| `typography` | 标题占约 40% 以上，辅助图形克制 | 评论、观点、金句 |
| `metaphor` | 用具体物体或场景表达抽象主题 | 成长、哲思、个人发展 |
| `scene` | 环境、光线和人物动作形成叙事氛围 | 故事、旅行、生活方式 |
| `minimal` | 单一焦点，至少约 60% 留白 | 极简、专注、核心概念 |

## 配色

| 标识 | 主色倾向 | 气质与用途 |
|---|---|---|
| `warm` | 橙、金黄、陶土、柔桃色 | 亲切、教育、产品、生活方式 |
| `elegant` | 柔珊瑚、灰蓝绿、淡玫瑰 | 精致、商业、文化和思想内容 |
| `cool` | 工程蓝、海军蓝、青色 | 技术、专业、系统和数据 |
| `dark` | 近黑、深紫、电光青和品红 | 电影感、高端、未来与夜景 |
| `earth` | 森林绿、鼠尾草、土棕 | 自然、健康、环保和成长 |
| `vivid` | 鲜红、亮绿、电光蓝 | 高能、活动、娱乐和强提醒 |
| `pastel` | 浅粉、薄荷、薰衣草 | 温柔、轻松、亲子和创意 |
| `mono` | 黑、近黑、白和灰 | 极简、聚焦、专业和文字主导 |
| `retro` | 哑橙、旧粉、酒红、芥末黄 | 怀旧、历史和复古科技 |
| `duotone` | 两种高对比或互补色 | 海报、戏剧性观点和文化主题 |
| `macaron` | 米白背景配浅蓝、薄荷、薰衣草、桃色 | 教育、知识卡片和手绘风格 |

背景、正文文字和主视觉必须保持对比。强调色通常不超过画面面积的 15%。

## 绘制方式

| 标识 | 线条与材质 | 适用内容 |
|---|---|---|
| `flat-vector` | 清晰轮廓、平涂、几何图标、少阴影 | 产品、知识和现代数字内容 |
| `hand-drawn` | 粗细不均线条、纸张纹理、轻微不规则 | 教育、个人表达和友好内容 |
| `painterly` | 软边、笔触、颜料晕染和自然光 | 旅行、故事、情绪和自然主题 |
| `digital` | 精确边缘、克制渐变、抛光数字质感 | 科技、商业、UI 与数据主题 |
| `pixel` | 像素网格、抖动色和块状轮廓 | 游戏、复古科技和数字文化 |
| `chalk` | 粉笔线、粉尘颗粒和黑板材质 | 教学、公式和课堂说明 |
| `screen-print` | 粗线、网点、有限色和套色偏移感 | 评论、海报、文化和戏剧性主题 |

## 文字密度

| 标识 | 内容 | 建议留白 |
|---|---|---|
| `none` | 无文字，纯视觉 | 约 100% 用于视觉 |
| `title-only` | 仅准确标题，默认 | 至少约 85% 保持非文字区域 |
| `title-subtitle` | 标题和原文已有副标题 | 至少约 75% 保持非文字区域 |
| `text-rich` | 标题、副标题和 2–4 个关键词 | 至少约 60% 保持非文字区域 |

除非用户明确提供，禁止自行生成副标题、标签和日期。移动端封面优先 `title-only`。

## 情绪强度

| 标识 | 对比与饱和度 | 适用场景 |
|---|---|---|
| `subtle` | 低对比、低饱和、轻量视觉 | 专业、冷静、反思和长文 |
| `balanced` | 中等对比和饱和度，默认 | 大多数文章和博客 |
| `bold` | 高对比、高饱和、动态构图 | 发布、活动、强观点和娱乐 |

## 字体气质

| 标识 | 特征 | 适用内容 |
|---|---|---|
| `clean` | 几何无衬线、清晰中性，默认 | 科技、商业和现代内容 |
| `handwritten` | 手写或笔刷感、自然变化 | 个人、教育和温暖主题 |
| `serif` | 经典衬线、精致稳重 | 编辑、文化、历史和权威内容 |
| `display` | 粗重、装饰性、强识别 | 娱乐、活动和短标题 |

中文标题不要求模型复刻特定商业字体，只描述黑体、宋体、手写或装饰性气质。

## 比例

| 比例 | 主要用途 |
|---|---|
| `2.35:1` | 博客头图、文章页横幅和电影感封面 |
| `16:9` | 通用横版、演示文稿和视频缩略图 |
| `4:3` | 信息稍多的传统横版 |
| `3:2` | 摄影感横版和图文卡片 |
| `1:1` | 社交媒体方形卡片 |
| `3:4` | 小红书、Pinterest 和移动端竖图 |

用户说明目标平台时优先按平台选比例；不明确时使用配置值，配置也未指定时使用 `16:9`。

## 兼容建议

- `hero`：优先 `digital`、`flat-vector`、`screen-print`；搭配 `title-only` 或 `title-subtitle`。
- `conceptual`：优先 `digital`、`flat-vector`、`hand-drawn`；搭配 `title-only`。
- `typography`：优先 `flat-vector`、`screen-print`、`digital`；搭配 `title-only` 或 `text-rich`。
- `metaphor`：优先 `hand-drawn`、`painterly`、`digital`；避免文字过多。
- `scene`：优先 `painterly`、`hand-drawn`、`digital`；搭配 `none` 或 `title-only`。
- `minimal`：优先 `flat-vector`、`digital`；搭配 `none` 或 `title-only`。
- `pixel` 与 `chalk` 不适合小字号副标题；`screen-print` 更适合短而有力的标题。
- `dark` 配色必须使用浅色文字；`pastel` 和 `macaron` 需要深色文字保证可读性。

## 风格预设

| 预设 | 配色 | 绘制方式 |
|---|---|---|
| `elegant` | `elegant` | `hand-drawn` |
| `blueprint` | `cool` | `digital` |
| `chalkboard` | `dark` | `chalk` |
| `dark-atmospheric` | `dark` | `digital` |
| `editorial-infographic` | `cool` | `digital` |
| `fantasy-animation` | `pastel` | `painterly` |
| `flat-doodle` | `pastel` | `flat-vector` |
| `intuition-machine` | `retro` | `digital` |
| `minimal` | `mono` | `flat-vector` |
| `nature` | `earth` | `hand-drawn` |
| `notion` | `mono` | `digital` |
| `pixel-art` | `vivid` | `pixel` |
| `playful` | `pastel` | `hand-drawn` |
| `retro` | `retro` | `digital` |
| `sketch-notes` | `warm` | `hand-drawn` |
| `vector-illustration` | `retro` | `flat-vector` |
| `vintage` | `retro` | `hand-drawn` |
| `warm-flat` | `warm` | `flat-vector` |
| `hand-drawn-edu` | `macaron` | `hand-drawn` |
| `watercolor` | `earth` | `painterly` |
| `poster-art` | `retro` | `screen-print` |
| `mondo` | `mono` | `screen-print` |
| `art-deco` | `elegant` | `screen-print` |
| `propaganda` | `vivid` | `screen-print` |
| `cinematic` | `duotone` | `screen-print` |

预设只是配色和绘制方式的快捷组合，用户明确传入的 `--palette` 或 `--rendering` 可以覆盖对应部分。

## 自动选择

### 类型

- 发布、品牌、重磅消息：`hero`。
- 架构、模型、抽象方法：`conceptual`。
- 评论、金句、标题本身是焦点：`typography`。
- 成长、突破、转变和哲思：`metaphor`。
- 故事、人物、旅行和体验：`scene`。
- 专注、极简和单一概念：`minimal`。

### 配色

- 技术、系统、数据：`cool`。
- 商业、文化、思想：`elegant`。
- 教育、团队、产品：`warm` 或 `macaron`。
- 自然、健康、环保：`earth`。
- 游戏、活动和流行文化：`vivid` 或 `dark`。
- 历史和怀旧：`retro`。
- 没有强信号时：`elegant` 或 `warm`，避免随机使用高饱和色。

### 绘制、文字、情绪与字体

- 技术和商业默认 `digital + title-only + balanced + clean`。
- 教育和个人内容默认 `hand-drawn + title-only + balanced + handwritten`。
- 旅行和叙事默认 `painterly + title-only + subtle + serif`。
- 强观点和活动默认 `screen-print + title-only + bold + display`。
- 标题超过约 18 个汉字时，优先缩小文字密度或改用无标题封面，不擅自缩写标题。
