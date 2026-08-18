# 封面偏好配置

偏好保存在 `EXTEND.md`。当前请求中的明确参数始终优先于配置。

## 查找顺序

1. `.marc-skills/article-cover-image/EXTEND.md`
2. `${XDG_CONFIG_HOME:-$HOME/.config}/marc-skills/article-cover-image/EXTEND.md`
3. `$HOME/.marc-skills/article-cover-image/EXTEND.md`

第一个存在的文件生效。没有配置时直接采用默认值，不强制创建。

## 完整格式

```yaml
watermark:
  enabled: false
  content: ""
  position: bottom-right

preferred_type: null
preferred_palette: null
preferred_rendering: null
preferred_text: title-only
preferred_mood: balanced
preferred_font: clean
default_aspect: "16:9"
default_output_dir: independent
quick_mode: false
language: null
preferred_image_backend: auto

custom_palettes: []
```

## 字段

| 字段 | 类型 | 默认值 | 说明 |
|---|---|---|---|
| `watermark.enabled` | 布尔 | `false` | 是否要求水印 |
| `watermark.content` | 字符串 | 空 | 水印内容 |
| `watermark.position` | 枚举 | `bottom-right` | `bottom-right`、`bottom-left`、`bottom-center`、`top-right` |
| `preferred_type` | 字符串或空 | `null` | 默认构图类型；空表示自动判断 |
| `preferred_palette` | 字符串或空 | `null` | 默认配色 |
| `preferred_rendering` | 字符串或空 | `null` | 默认绘制方式 |
| `preferred_text` | 字符串 | `title-only` | 默认文字密度 |
| `preferred_mood` | 字符串 | `balanced` | 默认情绪强度 |
| `preferred_font` | 字符串 | `clean` | 默认字体气质 |
| `default_aspect` | 字符串 | `16:9` | 默认比例 |
| `default_output_dir` | 枚举 | `independent` | `independent`、`same-dir`、`imgs-subdir` |
| `quick_mode` | 布尔 | `false` | 是否长期跳过确认 |
| `language` | 字符串或空 | `null` | 标题语言；空表示跟随原文 |
| `preferred_image_backend` | 字符串 | `auto` | `auto`、`ask` 或当前环境中的后端标识 |
| `custom_palettes` | 数组 | `[]` | 自定义配色 |

## 自定义配色

```yaml
custom_palettes:
  - name: corporate-tech
    description: 克制、可信的企业技术配色
    colors:
      primary: ["#16324F", "#2A6F97"]
      background: "#F7FAFC"
      accents: ["#61A5C2"]
    decorative_hints: [细网格, 数据节点, 轻微渐变]
    best_for: [企业技术, 数据报告]
```

`name` 使用小写英文和连字符。自定义配色不得使用无权使用的品牌名。

## 修改规则

- 用户要求永久保存偏好时，先确认保存位置，再创建或更新文件。
- 用户只为当前封面指定选项时，不写入配置。
- `quick_mode: true` 是长期跳过确认的设置，只在用户明确要求时写入。
- 固定后端不可用时改用自动选择，并向用户说明。
- 水印默认关闭；没有用户提供的水印内容时不得自动开启。
