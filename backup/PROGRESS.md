# 文档整理进度

> 过程文档, 位于 `AiKv-Workflow/backup/`. aidb / aikv 仓库内不维护此表.

**当前阶段**: 文档整理 ✅ — 后续开发见 [PLAN-dev.md](PLAN-dev.md) (**v1 实施计划**)

**新会话提示词**: 文档整理见 [SESSION-PROMPT.md](SESSION-PROMPT.md); **开发实施**见 [PLAN-SESSION-PROMPT.md](PLAN-SESSION-PROMPT.md).

**写作顺序 (已确认)**:

- **阶段 1**: aidb + aikv 全部 modules, 按依赖单链 12 步 (见 `design.md`)
- **阶段 2a**: aidb 根文档汇总 · **阶段 2b**: aikv 根文档汇总
- **每章**: 流程 0–4; **每步与你讨论确认后再执行下一步** (见 `design.md` 确认门控)

---

## Step 0: 文档骨架

- [x] 用户确认 `design.md` 中的目标文档结构
- [x] 用户确认 modules 划分 (engine 拆分, commands 拆分)
- [x] 用户确认每章流程 (0–4) 与 ISSUES 约定
- [x] 用户确认 Module Skill 内容格式 (路径不变, 正文按 Skill 标准, 日后仅迁位置)
- [x] aidb/aikv 旧文档移入 `backup/{aidb,aikv}/`
- [x] aidb: 新建根目录文档 (README, ARCHITECTURE, DESIGN, DEPLOYMENT, CHANGELOG, CONTRIBUTING) — 可先占位
- [x] aidb: `docs/README.md` (hub); `docs/development.md` 未建 (hub 链 DEPLOYMENT + CONTRIBUTING)
- [x] aidb: `docs/modules/` — engine, engine-storage, cluster, backup, observability (5 篇)
- [x] aikv: 新建根目录文档 (README, ARCHITECTURE, DESIGN, DEPLOYMENT, CHANGELOG, CONTRIBUTING)
- [x] aikv: `docs/README.md` (hub); `docs/development.md` 未建 (hub 链 DEPLOYMENT + CONTRIBUTING)
- [x] aikv: `docs/modules/` — protocol, server, storage, commands-core, commands-extended, cluster, observability (7 篇)

---

## 阶段 1: modules (步 1–12, 全部 ✅ 后再进入阶段 2)

| 步 | 仓库 | 章节 | 覆盖 src | 状态 | 完成日期 |
|----|------|------|----------|------|----------|
| 1 | aidb | `docs/modules/engine.md` | wal, memtable, db | ✅ 完成 | 2026-06-17 |
| 2 | aidb | `docs/modules/engine-storage.md` | sstable, compaction, filter, cache, checkpoint | ✅ 完成 | 2026-06-17 |
| 3 | aikv | `docs/modules/protocol.md` | protocol/* | ✅ 完成 | 2026-06-18 |
| 4 | aikv | `docs/modules/server.md` | server/* | ✅ 完成 | 2026-06-18 |
| 5 | aidb | `docs/modules/cluster.md` | cluster/* | ✅ 完成 | 2026-06-18 |
| 6 | aikv | `docs/modules/storage.md` | storage/* | ✅ 完成 | 2026-06-18 |
| 7 | aikv | `docs/modules/commands-core.md` | string~router | ✅ 完成 | 2026-06-18 |
| 8 | aikv | `docs/modules/commands-extended.md` | json~server cmd | ✅ 完成 | 2026-06-18 |
| 9 | aidb | `docs/modules/backup.md` | backup/* | ✅ 完成 | 2026-06-18 |
| 10 | aidb | `docs/modules/observability.md` | metrics, monitoring | ✅ 完成 | 2026-06-18 |
| 11 | aikv | `docs/modules/cluster.md` | cluster/* | ✅ 完成 | 2026-06-18 |
| 12 | aikv | `docs/modules/observability.md` | slowlog, metrics, info | ✅ 完成 | 2026-06-18 |

状态: ⬜ 待开始 | 🔄 进行中 | ✅ 完成

---

## 阶段 2a: aidb 汇总 (步 13–18, 阶段 1 全部 ✅ 后)

| 步 | 章节 | 状态 | 完成日期 |
|----|------|------|----------|
| 13 | `ARCHITECTURE.md` | ✅ 完成 | 2026-06-18 |
| 14 | `DESIGN.md` | ✅ 完成 | 2026-06-18 |
| 15 | `DEPLOYMENT.md` | ✅ 完成 | 2026-06-18 |
| 16 | `README.md` | ✅ 完成 | 2026-06-18 |
| 17 | `CONTRIBUTING.md` / `CHANGELOG.md` | ✅ 完成 | 2026-06-18 |
| 18 | `docs/README.md` (导航) | ✅ 完成 | 2026-06-18 |

`docs/development.md`: 未单独创建; hub 链 DEPLOYMENT + CONTRIBUTING (步 18 A1).

---

## 阶段 2b: aikv 汇总 (步 19–24, 阶段 2a 完成后)

| 步 | 章节 | 状态 | 完成日期 |
|----|------|------|----------|
| 19 | `ARCHITECTURE.md` | ✅ 完成 | 2026-06-18 |
| 20 | `DESIGN.md` | ✅ 完成 | 2026-06-18 |
| 21 | `DEPLOYMENT.md` | ✅ 完成 | 2026-06-18 |
| 22 | `README.md` | ✅ 完成 | 2026-06-18 |
| 23 | `CONTRIBUTING.md` / `CHANGELOG.md` | ✅ 完成 | 2026-06-18 |
| 24 | `docs/README.md` (导航) | ✅ 完成 | 2026-06-18 |

`docs/development.md`: 未单独创建; hub 链 DEPLOYMENT + CONTRIBUTING (步 24 A1).

---

## Step 3: 验收

- [x] 阶段 1: 12 篇 modules 全部 ✅
- [x] 阶段 2a: aidb 根文档与 `docs/README.md` 全部 ✅
- [x] 阶段 2b: aikv 根文档与 `docs/README.md` 全部 ✅
- [x] 主观测试: 仅凭新文档可定位功能代码 (用户自验后勾选)

---

## Step 4: 清理旧仓库

> **2026-06-18 用户决定**: 保留旧/工具仓库作只读参考, **不执行删除**. 日常开发以 aidb/aikv 新文档为准.

- [x] ~~删除 aidb-oldmain~~ — 保留
- [x] ~~删除 aikv-oldmain~~ — 保留
- [x] ~~删除 wiqun-db~~ — 保留
- [x] ~~删除 wiqun-kv~~ — 保留
- [x] ~~删除 wiqun-factory~~ — 保留
- [x] ~~删除 WiQunTools~~ — 保留
- [x] ~~(可选) 清理 `backup/archive/`~~ — 保留
