# 默认排版设计令牌与元素样式规格

无额外偏好时的默认设计：专业、克制、简洁、现代。

## 基础令牌

| 项 | 值 |
|---|---|
| 正文字号 | 16px |
| 正文行高 | 1.8 |
| 正文颜色 | `#333333` |
| 辅助文字颜色 | `#777777` |
| 主题色 | `#2563EB` |
| 段落间距 | 16px |
| 一级内容标题 | 20~22px |
| 二级内容标题 | 18~20px |
| 图片上下间距 | 20px |

字体栈（所有文字元素）：

```css
font-family:-apple-system,BlinkMacSystemFont,"Helvetica Neue","PingFang SC","Microsoft YaHei",Arial,sans-serif;
```

## 元素样式参考（全部写为内联 style）

### 正文段落

```html
<p style="margin:0 0 16px;font-size:16px;line-height:1.8;color:#333333;word-break:break-word;">正文内容</p>
```

### 一级内容标题（H1 视觉）

```html
<p style="margin:24px 0 16px;font-size:21px;font-weight:700;line-height:1.5;color:#1a1a1a;word-break:break-word;">标题文字</p>
```

### 二级内容标题（H2 视觉）

```html
<p style="margin:20px 0 12px;font-size:18px;font-weight:700;line-height:1.5;color:#1a1a1a;word-break:break-word;">小标题文字</p>
```

### 加粗 / 斜体

```html
<strong style="color:#333333;">加粗内容</strong>
<em style="color:#333333;">斜体内容</em>
```

### 引用块

```html
<blockquote style="margin:0 0 16px;padding:12px 16px;background-color:#f5f7fa;border-left:4px solid #2563EB;color:#555555;font-size:15px;line-height:1.8;border-radius:0 6px 6px 0;">
  引用内容
</blockquote>
```

### 无序 / 有序列表

```html
<ul style="margin:0 0 16px;padding-left:24px;color:#333333;font-size:16px;line-height:1.8;">
  <li style="margin:6px 0;">列表项</li>
</ul>
```

### 图片

```html
<img src="图片URL" alt="替代文字" style="display:block;width:100%;max-width:100%;height:auto;margin:20px auto;border-radius:4px;" />
```

### 分隔线

```html
<hr style="margin:20px 0;border:0;border-top:1px solid #eeeeee;" />
```

### 表格

```html
<table style="width:100%;max-width:100%;margin:0 0 16px;border-collapse:collapse;font-size:14px;line-height:1.6;color:#333333;word-break:break-word;">
  <tbody>
    <tr>
      <td style="border:1px solid #e0e0e0;padding:8px 10px;background-color:#f7f9fc;font-weight:600;">表头单元格</td>
    </tr>
    <tr>
      <td style="border:1px solid #e0e0e0;padding:8px 10px;">单元格</td>
    </tr>
  </tbody>
</table>
```

### 代码块

```html
<pre style="margin:0 0 16px;padding:14px 16px;background-color:#f6f8fa;border:1px solid #e8e8e8;border-radius:6px;overflow-x:auto;white-space:pre;font-size:14px;line-height:1.6;color:#333333;"><code>代码内容（原样保留空格、缩进、换行）</code></pre>
```

行内代码：

```html
<code style="font-size:0.9em;background-color:#f0f0f0;padding:2px 5px;border-radius:3px;color:#c7254e;">行内代码</code>
```

## 装饰元素约束

纯装饰元素必须满足：不含任何新增文字；删除后不影响文章理解；不依赖定位和动画；不喧宾夺主；深色环境下仍具基本可读性；即使被微信过滤，文章结构仍完整。

## 风格与硬性约束

- 不使用花哨动画、复杂阴影、大面积高饱和色。
- 不添加原文中不存在的装饰文字。
- 不依赖 `display:flex/grid`、`position`、`transform` 等实现核心结构。
- 主题色仅作点缀（标题装饰线、引用左边框、链接色等），不用作大面积填充。
