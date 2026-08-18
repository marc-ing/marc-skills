---
name: conventional-commit
description: 根据 Git 变更生成或检查 Conventional Commits 风格的提交信息。用户要求写 commit message、总结暂存区改动或验证提交格式时使用。
---

# Conventional Commit 提交信息

只负责生成和检查提交信息。除非用户明确要求提交，否则不要执行 git add 或 git commit。

## 工作流程

1. 优先读取 git diff --cached；暂存区为空时，再查看 git diff 并明确说明依据。
2. 查看最近几条提交，沿用仓库已有的语言、scope 和大小写习惯。
3. 识别变更的主要目的，不要只按文件名猜测。
4. 生成最小且准确的提交信息；混合多个无关目的时，建议拆分提交。

## 格式

使用“type(scope): summary”，scope 可省略，破坏性变更在 type 或 scope 后添加感叹号。

常用 type：

| type | 用途 |
| --- | --- |
| feat | 新功能 |
| fix | 缺陷修复 |
| docs | 仅文档 |
| style | 不影响逻辑的格式调整 |
| refactor | 非功能、非修复的代码重构 |
| perf | 性能改进 |
| test | 测试 |
| build | 构建系统或依赖 |
| ci | 持续集成 |
| chore | 其他维护工作 |
| revert | 回退提交 |

## 写作规则

- summary 使用简短的祈使表达，准确说明完成了什么。
- 沿用仓库语言；无法判断时使用英文。
- 首行尽量不超过 72 个字符，不以句号结尾。
- scope 只在能帮助定位模块时使用。
- 需要解释原因、迁移方式或副作用时添加正文。
- 破坏性变更在页脚写明 BREAKING CHANGE。
- 只有从上下文确认关联编号时才添加 Closes 或 Refs，不要猜测。

默认只输出可直接使用的提交信息。用户要求检查时，指出不符合项并给出修正版。
