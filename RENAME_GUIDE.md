# 名称修改对照表

本文档记录了所有从 Claude Code 修改为 OH-code 的地方，供需要还原或自定义修改参考。

---

## 1. package.json

| 原值 | 新值 |
|------|------|
| `@anthropic-ai/claude-code` | `@douyin-oh/oh-code` |
| `claude` (bin) | `oh` (bin) |
| `2.1.88` | `1.0.0` |
| `Anthropic <support@anthropic.com>` | `douyin-OH <support@example.com>` |
| `SEE LICENSE IN README.md` | `MIT` |
| `Use Claude, Anthropic's AI assistant...` | `An AI-powered coding assistant...` |
| `https://github.com/anthropics/claude-code` | (删除) |
| `https://github.com/anthropics/claude-code/issues` | (删除) |

---

## 2. README.md

完全重写，删除了所有 Claude Code、Anthropic 相关内容和链接。

---

## 3. LICENSE.md

从 Anthropic PBC 专有许可证改为 MIT 许可证，版权声明改为 "Copyright (c) 2024 douyin-OH"。

---

## 4. 代码中的用户可见文本

### src/history.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第35行注释 | `Claude Code parses history...` | `OH-code parses history...` |
| 第412行注释 | `Claude Code's Tungsten tool` | `the Tungsten tool` |

### src/ink/components/App.tsx

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第412行注释 | `Emit suspend event for Claude Code to handle` | `Emit suspend event to handle` |
| 第433行注释 | `Emit resume event for Claude Code to handle` | `Emit resume event to handle` |

### src/main.tsx

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第968行 | `program.name('claude')` | `program.name('oh')` |
| 第968行 | `Claude Code - starts an interactive session...` | `OH-code - starts an interactive session...` |
| 第1022行 | `Tip: You can launch Claude Code with just 'claude'` | `Tip: You can launch OH-code with just 'oh'` |
| 第3808行 | `${MACRO.VERSION} (Claude Code)` | `${MACRO.VERSION} (OH-code)` |
| 第3895行 | `Start the Claude Code MCP server` | `Start the OH-code MCP server` |
| 第3962行 | `Start a Claude Code session server` | `Start an OH-code session server` |
| 第4046行 | `Run Claude Code on a remote host...` | `Run OH-code on a remote host...` |
| 第4050行 | `Usage: claude ssh...` / `Runs Claude Code...` | `Usage: oh ssh...` / `Runs OH-code...` |
| 第4059行 | `Connect to a Claude Code server` | `Connect to an OH-code server` |
| 第4148行 | `Manage Claude Code plugins` | `Manage OH-code plugins` |
| 第4171行 | `Manage Claude Code marketplaces` | `Manage OH-code marketplaces` |
| 第4346行 | `Check the health of your Claude Code...` | `Check the health of your OH-code...` |
| 第4395行 | `Install Claude Code native build` | `Install OH-code native build` |
| 第4101行 | `Sign in to your Anthropic account` | `Sign in to your account` |
| 第4101行 | `Use Anthropic Console` / `Claude subscription` | `Use Console` / `subscription` |
| 第4131行 | `Log out from your Anthropic account` | `Log out from your account` |

### src/commands.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第193行 | `Generate a report analyzing your Claude Code sessions` | `Generate a report analyzing your coding sessions` |

### src/tools/WebFetchTool/utils.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第23行 | `Claude Code is unable to fetch from ${domain}` | `OH-code is unable to fetch from ${domain}` |

### src/tools/AgentTool/built-in/statuslineSetup.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第3行 | `You are a status line setup agent for Claude Code` | `You are a status line setup agent for OH-code` |
| 第3行 | `user's Claude Code settings` | `user's OH-code settings` |

### src/tools/AgentTool/built-in/generalPurposeAgent.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第3行 | `You are an agent for Claude Code, Anthropic's official CLI for Claude` | `You are an agent for OH-code` |

### src/tools/AgentTool/built-in/planAgent.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第21行 | `You are a software architect and planning specialist for Claude Code` | `You are a software architect and planning specialist for OH-code` |

### src/tools/AgentTool/built-in/claudeCodeGuideAgent.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第30行 | `You are the Claude guide agent...` | `You are the guide agent...` |
| 第34行 | `1. **Claude Code** (the CLI tool)` | (保留但内容为 Claude Code 相关) |
| 第36行 | `2. **Claude Agent SDK**` | (保留) |
| 第38行 | `3. **Claude API** (formerly known as the Anthropic API)` | (保留) |

### src/tools/AgentTool/built-in/exploreAgent.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第24行 | `You are a file search specialist for Claude Code, Anthropic's official CLI for Claude` | `You are a file search specialist for OH-code` |

### src/tools/ConfigTool/prompt.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第9行 | `Get or set Claude Code configuration settings` | `Get or set OH-code configuration settings` |
| 第50行 | `Get or set Claude Code configuration settings` | `Get or set OH-code configuration settings` |
| 第52行 | `View or change Claude Code settings` | `View or change OH-code settings` |

### src/tools/ConfigTool/ConfigTool.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第69行 | `get or set Claude Code settings (theme, model)` | `get or set OH-code settings (theme, model)` |

### src/tools/FileReadTool/prompt.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第40行 | `This tool allows Claude Code to read images` | `This tool allows reading images` |
| 第40行 | `as Claude Code is a multimodal LLM` | `as OH-code is a multimodal LLM` |

### src/tools/PowerShellTool/pathValidation.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第1763行 | `For security, Claude Code may only access files...` | `For security, OH-code may only access files...` |
| 第1876行 | `For security, Claude Code may only access files...` | `For security, OH-code may only access files...` |
| 第1963行 | `For security, Claude Code may only write...` | `For security, OH-code may only write...` |
| 第2016行 | `For security, Claude Code may only write...` | `For security, OH-code may only write...` |

### src/tools/BashTool/pathValidation.ts

| 位置 | 原文本 | 新文本 |
|------|--------|--------|
| 第622行 | `For security, Claude Code cannot automatically validate...` | `For security, OH-code cannot automatically validate...` |

---

## 5. 未能修改的内容

以下内容涉及功能性依赖或 API 端点，修改会导致功能异常：

- `@anthropic-ai/sdk` - npm 包依赖，不可更改
- `api.anthropic.com` - API 端点地址
- `github.com/anthropics/*` - 预批准的安全域名
- `process.env.__CFBundleIdentifier === 'com.anthropic.claude-code-url-handler'` - macOS URL 处理程序标识
- `CLAUDE_CODE_*` - 环境变量名称
- `com.anthropic.*` - macOS Bundle ID 相关配置

---

## 还原指南

如需将项目名还原为 Claude Code：

1. 将上述表格中的新值替换回原值
2. 将 README.md 和 LICENSE.md 恢复为原始内容
3. 将 package.json 恢复为原始内容
4. 全局搜索 `OH-code` 并替换为 `Claude Code`
5. 全局搜索 `oh` 并替换为 `claude`（注意：需排除单词内的 `oh`，如 `oh no`）

---

## 自定义修改建议

如果需要使用其他名称（如 `MyTool`）：

1. 将 `OH-code` → `MyTool`
2. 将 `oh` → `mytool` 或保留 `oh` 作为命令名
3. 将 `@douyin-oh/oh-code` → `@your-name/my-tool`
4. 更新 README.md 中的所有引用
5. 全局搜索验证无遗漏
