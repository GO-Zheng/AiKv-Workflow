# 后续开发 — 新会话开场模板

> 按 [PLAN-dev.md](PLAN-dev.md) **v1 三线路** 实施时, **每个里程碑开新对话** 复制下方模板, 只改 `【…】`.  
> 工作目录: `/root/code/database`

---

## 开新对话前 (~30 秒)

1. 看 [PLAN-dev.md](PLAN-dev.md) — 当前做到哪条 checklist  
2. 看 [TODO.md](TODO.md) — 若线路 A, 确认 ISSUE 编号  
3. 填好下方 5 项 → 粘贴到新对话

---

## 开场模板 (复制从这里开始)

```markdown
## 后续开发 — 【线路 A|B|C · 里程碑名】

工作目录: `/root/code/database`

请先阅读 (不要跳过):
1. `AiKv-Workflow/backup/PLAN-dev.md` — v1 三线路与 checklist
2. `AiKv-Workflow/backup/TODO.md` — 若含 ISSUES
3. 【可选: `aidb/ISSUES.md` / `aikv/ISSUES.md` / 相关 module 文档】

---

### 本次任务

| 项 | 值 |
|----|-----|
| 线路 | 【A ISSUES / B 测试 / C monitor】 |
| 里程碑 | 【如: 阶段1 · B1+A1 P0 / C1 栈迁移 / B2 testviz v0】 |
| 目标仓库/路径 | 【如: `aidb/`, `aikv/`, `AiFactory/monitor/`】 |
| 具体条目 | 【如: ISSUE-001+002; 或 C1.1–C1.3】 |
| 分支 | 【如: `fix/aidb-wal-001` / 新建】 |

### 必须遵守

- 小步 PR: 只做本次里程碑范围, 不扩 scope  
- 每条 ISSUE: 复现测试 → 修/关 → 更新对应 `ISSUES.md`  
- 监控: aidb **无** HTTP/OTel; metrics 走 aikv OTLP (C2); logs JSON+Alloy  
- 过程计划更新 `PLAN-dev.md` checklist; **不要** commit 除非我明确要求  

### 本次不要

- 【填写: 如不要动 testviz / 不要改 monitor compose / …】

---

请先给出本里程碑 **实施步骤与风险**, 等我确认后再写代码。
```

---

## 线路速查

| 线路 | 里程碑示例 | 主要路径 |
|------|------------|----------|
| **A** | A1 P0 | aidb 001/002/005, aikv 002 |
| **B** | B1 基建 | CONTRIBUTING, WAL/Options 测试 |
| **B** | B2-v0 | `AiFactory/testviz/` 扫描+跑测 |
| **C** | C1 | `AiFactory/monitor/`, Alloy, 文档 |
| **C** | C2 | aikv OTel metrics, exemplars, 关联 |
| **C** | C2.6 | ✅ 移除 scrape, OTLP-only metrics |
| **C** | C3 | Pyroscope + eBPF profiles |
| **B** | B2-v0.1 | `AiFactory/testviz/` e2e/pytest 全量索引 |
| **B** | B2-v1 | `AiFactory/testviz/` Map + `@component` |
| **B** | B1.1+B1.4 | CONTRIBUTING 回归测 + CI 慢测矩阵 |

---

## 结束会话时 (Agent)

1. 更新 [PLAN-dev.md](PLAN-dev.md) 对应 `[ ]` → `[x]` (若完成)  
2. 更新 `ISSUES.md` / `CHANGELOG` (若改代码)  
3. 输出 **下一会话开场** — 已填好的模板  
4. **不要 commit**, 除非用户明确要求  

---

## 相关

| 文件 | 用途 |
|------|------|
| [PLAN-dev.md](PLAN-dev.md) | v1 实施计划 + Mermaid 顺序 |
| [TODO.md](TODO.md) | ISSUES 优先级 |
| [SESSION-PROMPT.md](SESSION-PROMPT.md) | 文档整理阶段 (已完成) 用 |
