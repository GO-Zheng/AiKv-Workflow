# 文档整理 — 新会话提示词

> 每篇 module (或阶段 2 汇总文档) **开新对话时** 复制下方「开场模板」, 只改 `【…】` 占位符.  
> 连续性靠 **本文件 + `design.md` + `PROGRESS.md` + `INDEX.md`**, 不靠聊天记忆.

工作目录: `/root/code/database`

---

## 开新对话前 (你, ~30 秒)

1. 看 `PROGRESS.md` — 上一篇是否 ✅; 若中断, 行内注明 `🔄 续: 步 N`
2. 填好下方「开场模板」里的 4 项变量
3. 粘贴到新对话发送

---

## 开场模板 (复制从这里开始)

```markdown
## 文档整理 — 新会话

工作目录: `/root/code/database`

请先阅读 (不要跳过):
1. `AiKv-Workflow/backup/design.md` — 总规程
2. `AiKv-Workflow/backup/PROGRESS.md` — 当前进度
3. `AiKv-Workflow/backup/INDEX.md` — 本章索引 (若已有行则更新)

---

### 本次任务

| 项 | 值 |
|----|-----|
| PROGRESS 总步 | 【如: 1 — 见 PROGRESS 阶段 1 表】 |
| 目标文件 | 【如: `aidb/docs/modules/engine.md`】 |
| 本次子步 | 【从步 0 开始 \| 续步 2 \| 步 4 草稿待确认】 |
| 对比深度 | 【模块级 \| 核心章逐段 — 见 design.md 对比深度表】 |

### 必须遵守

- **确认门控**: 步 0→1→2→3→4, 每步先讨论, 我确认后再下一步
- **步 4**: 先出 Module Skill 正文 **草稿**, 我确认后再写入 aidb/aikv、更新 INDEX/PROGRESS
- **Module Skill 基础模板**: frontmatter `name` + `description` (含 `Use when`); 见 `design.md`
- **过程只进 backup/**: INDEX、ISSUES; aidb/aikv 不写迁移历史
- **旧文档顺序**: `backup/{aidb,aikv}/` → `*-oldmain` → WiQunTools 查漏 → wiqun-*
- **待核实**: module 一行引用; 详情 `ISSUES.md`
- **步 4 落盘前**: 对照 create-skill Summary Checklist 自检 (见 `design.md`)

### 本次不要

- 不要跳过未确认的步骤
- 不要一次写多篇 module
- 不要修改 `design.md` / 流程, 除非我明确要求
- 不要 commit, 除非我明确要求

---

请从【步 0 | 步 N】开始, 给出本步交付物, 等我确认。
```

---

## 子步 0–4 速查 (每步 Agent 应交付什么)

| 子步 | 名称 | 确认前交付物 |
|------|------|----------------|
| 0 | 定范围 | 本章 `src/` 路径 + 入口文件列表 + 边界 (不覆盖哪些 module) |
| 1 | 读新代码 | 职责要点、代码地图表、主流程 bullet; 必要时 test 命令 |
| 2 | 查旧文档 | 参考过的旧文档路径 + 仍有效/过时/偏离/待核实 分类; 拟写 ISSUES |
| 3 | 对比旧代码 | 模块级差异 (核心章可加关键文件逐段); 文档应如何表述的建议 |
| 4 | 写文档 | **Module Skill 正文草稿** → 确认后落盘 + INDEX ✅ + 消化旧文档 + PROGRESS ✅ |

核心章逐段对比 (步 3): aidb `engine`, `engine-storage`, `cluster`; aikv `storage`, `cluster`.

---

## 结束会话时 (Agent 应做)

1. 更新 `PROGRESS.md` (状态 / 完成日期 / 若未完成则 `🔄 续: 步 N`)
2. 更新 `INDEX.md` 本章行
3. 若有新疑点, 更新 `ISSUES.md`
4. 输出 **「下一会话开场」** — 已填好的开场模板 (复制即用)
5. **不要 commit**, 除非用户明确要求

---

## 填空示例

### 示例 A — 第一篇 (aidb engine, 从头)

| 项 | 值 |
|----|-----|
| PROGRESS 总步 | 1 |
| 目标文件 | `aidb/docs/modules/engine.md` |
| 本次子步 | 从步 0 开始 |
| 对比深度 | 核心章逐段 |

开场句: `请从步 0 开始, 给出本步交付物, 等我确认。`

### 示例 B — 中断后续 (同一篇, 从步 3)

| 项 | 值 |
|----|-----|
| PROGRESS 总步 | 1 |
| 目标文件 | `aidb/docs/modules/engine.md` |
| 本次子步 | 续步 3 (步 0–2 已在 INDEX/上轮确认) |
| 对比深度 | 核心章逐段 |

开场句: `请先快速对照 INDEX 中本章已有记录, 从步 3 开始, 等我确认。`

### 示例 C — 阶段 2 汇总 (aidb ARCHITECTURE)

| 项 | 值 |
|----|-----|
| PROGRESS 总步 | 13 |
| 目标文件 | `aidb/ARCHITECTURE.md` |
| 本次子步 | 从步 0 开始 |
| 对比深度 | 模块级 (汇总文档) |

---

## 下一会话开场 (模板 — 由 Agent 在结束时填写)

```markdown
## 文档整理 — 新会话

工作目录: `/root/code/database`
请先读 `design.md`、`PROGRESS.md`、`INDEX.md`.

本次任务:
- PROGRESS 总步: 【】
- 目标文件: 【】
- 本次子步: 【】
- 对比深度: 【】

遵守 design.md 确认门控与 Module Skill 基础模板。从步 【】 开始, 等我确认。
```

---

## 相关文件

| 文件 | 用途 |
|------|------|
| [design.md](design.md) | 总规程、基础模板、章节顺序 |
| [PROGRESS.md](PROGRESS.md) | 步号与 ✅ 状态 |
| [INDEX.md](INDEX.md) | 旧文档参考与处理 |
| [ISSUES.md](ISSUES.md) | 待核实详情 |
