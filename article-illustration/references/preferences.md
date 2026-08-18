# 配图偏好配置

偏好保存在 `EXTEND.md`。配置只提供默认建议，用户当前请求始终具有更高优先级。

## 查找顺序

1. `.marc-skills/article-illustration/EXTEND.md`
2. `${XDG_CONFIG_HOME:-$HOME/.config}/marc-skills/article-illustration/EXTEND.md`
3. `$HOME/.marc-skills/article-illustration/EXTEND.md`

第一个存在的文件生效。不存在时直接使用默认值，不强制创建。

## 完整格式

```yaml
watermark:
  enabled: false
  content: ""
  position: bottom-right

preferred_type: null
preferred_style: sketch-notes
preferred_palette: macaron
language: null
default_output_dir: imgs-subdir
preferred_image_backend: auto
generation_batch_size: 4

custom_styles: []
```

## 字段

| 字段 | 类型 | 默认值 | 说明 |
|---|---|---|---|
| `watermark.enabled` | 布尔 | `false` | 是否要求生成水印 |
| `watermark.content` | 字符串 | 空 | 水印文字 |
| `watermark.position` | 枚举 | `bottom-right` | `bottom-right`、`bottom-left`、`bottom-center`、`top-right` |
| `preferred_type` | 字符串或空 | `null` | 默认配图类型；空表示自动判断 |
| `preferred_style` | 字符串或空 | `sketch-notes` | 默认风格 |
| `preferred_palette` | 字符串或空 | `macaron` | 默认配色；空表示使用风格配色 |
| `language` | 字符串或空 | `null` | 图中文字语言；空表示跟随文章 |
| `default_output_dir` | 枚举 | `imgs-subdir` | 输出目录策略 |
| `preferred_image_backend` | 字符串 | `auto` | `auto`、`ask` 或当前环境中的后端标识 |
| `generation_batch_size` | 整数 | `4` | 并行生成数量，限制为 1–8 |
| `custom_styles` | 数组 | `[]` | 用户自定义风格 |

## 自定义风格

```yaml
custom_styles:
  - name: corporate-tech
    description: 克制、专业的企业技术插画
    color_palette:
      primary: ["#16324F", "#2A6F97"]
      background: "#F7FAFC"
      accents: ["#61A5C2"]
    visual_elements: [网格, 模块, 数据流]
    typography: 简洁无衬线
    best_for: [企业技术, 架构说明]
```

`name` 使用小写英文和连字符。自定义风格不得冒用艺术家、工作室或受保护品牌的名称。

## 修改规则

- 用户要求永久修改偏好时，先确认保存位置，再创建或更新 `EXTEND.md`。
- 用户只在本次请求中指定选项时，不写入配置。
- `generation_batch_size` 的当次命令参数优先于配置。
- 固定后端不可用时改用自动选择，并向用户说明。
