# Claude Code Glob Tool 提示词

> 整理自 `src/tools/GlobTool/prompt.ts`
> 价值：文件模式匹配的最佳实践

---

## 目录

1. [原版英文](#原版英文)
2. [中文翻译](#中文翻译)
3. [价值解析](#价值解析)

---

## 原版英文

```markdown
# Glob Tool

- Fast file pattern matching tool that works with any codebase size
- Supports glob patterns like "**/*.js" or "src/**/*.ts"
- Returns matching file paths sorted by modification time
- Use this tool when you need to find files by name patterns
- When you are doing an open ended search that may require multiple rounds of globbing and grepping, use the Agent tool instead
```

---

## 中文翻译

```markdown
# Glob 工具

- 快速文件模式匹配工具，适用于任何规模的代码库
- 支持 glob 模式如 "**/*.js" 或 "src/**/*.ts"
- 返回按修改时间排序的匹配文件路径
- 当你需要按文件名模式查找文件时使用此工具
- 当你进行可能需要多轮 glob 和 grep 的开放式搜索时，改用 Agent 工具
```

---

## 价值解析

### 工具选择原则

| 任务 | 工具 |
|------|------|
| 按文件名查找 | ✅ Glob |
| 按内容查找 | ✅ Grep |
| 开放式/多轮搜索 | ✅ Agent tool |

### Glob 模式语法

| 模式 | 含义 | 示例 |
|------|------|------|
| `*` | 匹配路径分隔符以外的任意字符 | `*.js` → 所有 JS 文件 |
| `**` | 匹配任意路径（含嵌套） | `**/*.ts` → 所有 TS 文件 |
| `?` | 匹配单个字符 | `file?.js` → `file1.js` |
| `[abc]` | 匹配字符类 | `file[12].js` |
| `{a,b}` | 匹配多个模式 | `*.{js,ts}` |

### 返回值

```
Glob 返回的是：
├── 文件路径列表
└── 按修改时间排序（最新的在前）

适合的场景：
├── 查找"最近修改的文件"
├── 确认"文件是否存在"
└── 批量"读取某类文件"
```

### 对 AI 编程的启发

1. **按名索骥用 Glob**：当知道文件名模式时
2. **按内容索引用 Grep**：当知道文件内容时
3. **复杂搜索用 Agent**：当需要多轮推理时

---

*最后更新：2026年4月*
