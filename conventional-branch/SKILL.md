---
name: conventional-branch
description: 根据任务内容生成或检查 Conventional Branch 风格的 Git 分支名。用户要求给分支命名、创建功能分支，或验证 feature、bugfix、hotfix、release、chore 等前缀时使用。
---

# Conventional Branch 分支命名

只负责生成和检查分支名。除非用户明确要求，不创建、切换、重命名或删除分支。

## 命名格式

使用“类型/简短描述”：

| 类型 | 用途 |
| --- | --- |
| feature 或 feat | 新功能或功能增强 |
| bugfix 或 fix | 普通缺陷修复 |
| hotfix | 需要紧急上线的修复 |
| release | 发布准备 |
| chore | 依赖、文档、配置等维护工作 |

main、master 和 develop 是主干分支名，不添加类型前缀，也不要为普通任务重复创建。

## 生成规则

- 优先遵守当前仓库已有的命名规范；可先查看最近的分支名。
- 描述使用小写 kebab-case，通常控制在 2–5 个单词。
- 仅使用小写字母、数字和连字符。release 版本号可使用点号。
- 将空格和下划线改为连字符，合并连续连字符，并移除首尾连字符。
- 已知 issue 或工单号时，可放在描述开头，例如 feature/issue-123-add-login。
- 不清楚类型时，根据任务内容推断；只有确实无法判断时才询问用户。

## 检查规则

检查以下问题并给出修正后的名称：

- 类型不在允许范围内。
- 出现大写、空格、下划线或其他特殊字符。
- 描述过于笼统，例如 fix/bug 或 feature/new-feature。
- 存在连续连字符、连续点号或首尾分隔符。
- 非 release 分支在描述中使用点号。

默认只输出一个推荐名称和一句简短理由。用户要求多个方案时，再提供不超过三个候选。
