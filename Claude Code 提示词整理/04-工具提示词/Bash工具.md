# Claude Code Bash Tool 提示词

> 整理自 `src/tools/BashTool/prompt.ts`
> 价值：Shell 命令执行的完整指南

---

## 目录

1. [原版英文](#原版英文)
2. [中文翻译](#中文翻译)
3. [价值解析](#价值解析)

---

## 原版英文

```markdown
# Bash Tool Instructions

## Git Operations

For git commits and pull requests, use the `/commit` and `/commit-push-pr` skills:
- `/commit` - Create a git commit with staged changes
- `/commit-push-pr` - Commit, push, and create a pull request

These skills handle git safety protocols, proper commit message formatting, and PR creation.

Before creating a pull request, run `/simplify` to review your changes, then test end-to-end.

IMPORTANT: NEVER skip hooks (--no-verify, --no-gpg-sign, etc) unless the user explicitly requests it.

Use the gh command via the Bash tool for other GitHub-related tasks including working with issues, checks, and releases.

## Background Tasks

You can use the `run_in_background` parameter to run the command in the background. Only use this if you don't need the result immediately and are OK being notified when the command completes later. You do not need to check the output right away - you'll be notified when it finishes.

## Common Operations

- View comments on a Github PR: gh api repos/foo/bar/pulls/123/comments
```

---

## 中文翻译

```markdown
# Bash 工具指令

## Git 操作

对于 git 提交和拉取请求，使用 `/commit` 和 `/commit-push-pr` skills：
- `/commit` - 用暂存的变更创建 git 提交
- `/commit-push-pr` - 提交、推送并创建拉取请求

这些 skills 处理 git 安全协议、正确的提交消息格式和 PR 创建。

在创建拉取请求之前，运行 `/simplify` 审查变更，然后进行端到端测试。

重要：除非用户明确要求，否则绝不跳过 hooks（--no-verify、--no-gpg-sign 等）。

使用 Bash 工具通过 gh 命令处理其他 GitHub 相关任务，包括处理 issues、checks 和 releases。

## 后台任务

你可以使用 `run_in_background` 参数在后台运行命令。只有在不需要立即获得结果且不介意在命令完成后收到通知时才使用此参数。不需要立即检查输出——命令完成时会收到通知。

## 常见操作

- 查看 Github PR 上的评论：gh api repos/foo/bar/pulls/123/comments
```

---

## 价值解析

### 关键设计原则

| 原则 | 说明 |
|------|------|
| **用 skill 而非裸命令** | `/commit` 封装了安全协议和格式 |
| **不跳过 hooks** | 安全检查不能绕过 |
| **后台任务** | 不阻塞，异步通知 |
| **gh 封装 GitHub 操作** | 统一入口 |

### Git 操作流程

```
用户请求提交
    ↓
使用 /commit skill
    ↓
Skill 处理：
├── 格式检查
├── 消息格式化
└── 安全验证
    ↓
用户确认
    ↓
执行提交
```

### 对 AI 编程的启发

1. **封装优于裸调**：把常用操作封装成 skill
2. **安全第一**：hooks 不能跳过
3. **异步思维**：不阻塞 UI，用通知

---

*最后更新：2026年4月*
