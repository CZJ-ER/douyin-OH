# Claude Code Grep Tool 提示词

> 整理自 `src/tools/GrepTool/prompt.ts`
> 价值：代码搜索最佳实践

---

## 目录

1. [原版英文](#原版英文)
2. [中文翻译](#中文翻译)
3. [价值解析](#价值解析)

---

## 原版英文

```markdown
# Grep Tool

A powerful search tool built on ripgrep

## Usage

- ALWAYS use Grep for search tasks. NEVER invoke `grep` or `rg` as a Bash command. The Grep tool has been optimized for correct permissions and access.
- Supports full regex syntax (e.g., "log.*Error", "function\\s+\\w+")
- Filter files with glob parameter (e.g., "*.js", "**/*.tsx") or type parameter (e.g., "js", "py", "rust")
- Output modes: "content" shows matching lines, "files_with_matches" shows only file paths (default), "count" shows match counts
- Use Agent tool for open-ended searches requiring multiple rounds
- Pattern syntax: Uses ripgrep (not grep) - literal braces need escaping (use `interface\\{\\}` to find `interface{}` in Go code)
- Multiline matching: By default patterns match within single lines only. For cross-line patterns like `struct \\{[\\s\\S]*?field`, use `multiline: true`
```

---

## 中文翻译

```markdown
# Grep 工具

基于 ripgrep 的强大搜索工具

## 用法

- 始终使用 Grep 进行搜索任务。永远不要将 `grep` 或 `rg` 作为 Bash 命令调用。Grep 工具已经为正确的权限和访问进行了优化。
- 支持完整正则语法（如 "log.*Error"、"function\\s+\\w+"）
- 使用 glob 参数过滤文件（如 "*.js"、"**/*.tsx"）或 type 参数（如 "js"、"py"、"rust"）
- 输出模式："content" 显示匹配行，"files_with_matches" 仅显示文件路径（默认），"count" 显示匹配计数
- 对于需要多轮搜索的开放式搜索，使用 Agent 工具
- 模式语法：使用 ripgrep（不是 grep）——字面量括号需要转义（使用 `interface\\{\\}` 查找 Go 代码中的 `interface{}`）
- 多行匹配：默认情况下模式仅匹配单行内。对于跨行模式如 `struct \\{[\\s\\S]*?field`，使用 `multiline: true`
```

---

## 价值解析

### 工具选择原则

| 任务 | 工具 |
|------|------|
| 搜索文件内容 | ✅ Grep |
| ❌ 搜索文件内容 | ❌ Bash grep |
| 开放式搜索（多轮） | ✅ Agent tool |
| 按文件名查找 | ✅ Glob |

### Grep vs Bash grep

| 特性 | Grep 工具 | Bash grep |
|------|----------|-----------|
| 权限处理 | ✅ 自动处理 | ❌ 可能失败 |
| 输出模式 | 3种可选 | 需手动指定 |
| 多行匹配 | 支持 | 不支持 |
| 正则语法 | ripgrep | grep |

### 常见用法

```bash
# 搜索文件路径（默认）
Grep pattern: "function foo"

# 显示匹配行
Grep pattern: "log.*Error" output_mode: "content"

# 只显示文件列表
Grep pattern: "TODO" output_mode: "files_with_matches"

# 统计匹配数
Grep pattern: "class.*extends" output_mode: "count"

# Go 代码中的字面量匹配
Grep pattern: "interface\\\\{\\\\}" output_mode: "content"

# 多行匹配
Grep pattern: "struct \\\\{[\\\\s\\\\S]*?field" multiline: true
```

### 对 AI 编程的启发

1. **专用工具优先**：Grep 工具 > Bash grep
2. **权限自动化**：专用工具处理权限问题
3. **模式匹配**：根据任务选择正确的正则语法

---

*最后更新：2026年4月*
