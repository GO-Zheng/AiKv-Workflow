# 文档整理进度

> 过程文档, 位于 `AiKv-Workflow/backup/`. aidb / aikv 仓库内不维护此表.

**当前阶段**: Step 0 — 文档骨架待确认

---

## Step 0: 文档骨架

- [ ] 用户确认 `design.md` 中的目标文档结构
- [ ] aidb: 创建 `docs/README.md`, `docs/development.md`, `docs/modules/`
- [ ] aidb: 创建 `docs/modules/engine.md`, `cluster.md`
- [ ] aidb: 迁移 `AiKv-Workflow/backup/aidb/docs/observability.md` → `docs/modules/observability.md`
- [ ] aikv: 创建 `docs/README.md`, `docs/development.md`, `docs/modules/` (5 个 module 文件)

---

## Step 1–2: 按章完善

### aidb

| 顺序 | 章节 | 状态 | 完成日期 |
|------|------|------|----------|
| 1 | `docs/modules/engine.md` | ⬜ 待开始 | |
| 2 | `docs/modules/cluster.md` | ⬜ 待开始 | |
| 3 | `docs/modules/observability.md` | ⬜ 待开始 | |
| 4 | `ARCHITECTURE.md` 总审 | ⬜ 待开始 | |
| 5 | `DESIGN.md` 总审 | ⬜ 待开始 | |
| 6 | `DEPLOYMENT.md` 补充 | ⬜ 待开始 | |

### aikv

| 顺序 | 章节 | 状态 | 完成日期 |
|------|------|------|----------|
| 1 | `docs/modules/protocol.md` | ⬜ 待开始 | |
| 2 | `docs/modules/storage.md` | ⬜ 待开始 | |
| 3 | `docs/modules/commands.md` | ⬜ 待开始 | |
| 4 | `docs/modules/cluster.md` | ⬜ 待开始 | |
| 5 | `docs/modules/observability.md` | ⬜ 待开始 | |
| 6 | `ARCHITECTURE.md` 总审 | ⬜ 待开始 | |
| 7 | `DESIGN.md` 总审 | ⬜ 待开始 | |
| 8 | `DEPLOYMENT.md` 补充 | ⬜ 待开始 | |

状态: ⬜ 待开始 | 🔄 进行中 | ✅ 完成

---

## Step 3: 验收

- [ ] aidb 文档导航与模块文档验收通过
- [ ] aikv 文档导航与模块文档验收通过
- [ ] 主观测试: 仅凭新文档可定位功能代码

---

## Step 4: 清理旧仓库

- [ ] 删除 aidb-oldmain
- [ ] 删除 aikv-oldmain
- [ ] 删除 wiqun-db
- [ ] 删除 wiqun-kv
- [ ] 删除 wiqun-factory
- [ ] 删除 WiQunTools
- [ ] (可选) 清理 `AiKv-Workflow/backup/archive/` 内已无用的旧文档副本
