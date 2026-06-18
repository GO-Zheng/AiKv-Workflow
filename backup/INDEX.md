# 旧文档参考索引

> 记录「完善新文档时参考过哪些旧文档、如何处理」.  
> 过程文档, 位于 `AiKv-Workflow/backup/`, 不进入 aidb / aikv.  
> 待核实 / 可能 bug 详情见各仓库 [`aidb/ISSUES.md`](../../aidb/ISSUES.md)、[`aikv/ISSUES.md`](../../aikv/ISSUES.md); module 内一行引用即可.

**图例**: 处理 = `已删源` | `已归档` | `无有效内容跳过`

---

## aidb

| 新文档章节 | 状态 | 参考的旧文档 | 处理 | 备注 |
|------------|------|--------------|------|------|
| `docs/modules/engine.md` | ✅ | backup/aidb/ARCHITECTURE.md, DESIGN.md; WiQunTools 01-wal, 02-memtable, 04-db-engine, 08-snapshot | 已写 aidb/docs/modules/engine.md | ISSUE-001/002 |
| `docs/modules/engine-storage.md` | ✅ | backup/aidb/ARCHITECTURE,DESIGN + superpowers specs; WiQunTools 03–07, 13 §checkpoint; oldmain src 对照 | 已写 aidb/docs/modules/engine-storage.md | ISSUE-003/004 closed (doc-only) |
| `docs/modules/cluster.md` | ✅ | backup/aidb DESIGN,README,CONTRIBUTING; WiQunTools 09–12; oldmain REDIS_CLUSTER_COMPATIBILITY (概念); oldmain examples/cluster/README (反例) | 已写 aidb/docs/modules/cluster.md | ISSUE-005 open; 006–010 doc-only |
| `docs/modules/backup.md` | ✅ | backup/aidb {ARCHITECTURE,DESIGN,DEPLOYMENT,CHANGELOG,CONTRIBUTING}; WiQunTools 13 §1; oldmain src/backup + ADMIN_TOOL (过时跳过) | 已写 aidb/docs/modules/backup.md | ISSUE-011~013 doc-only |
| `docs/modules/observability.md` | ✅ | backup/aidb/docs/observability.md; DEPLOYMENT §; oldmain monitoring/* + MONITORING_GUIDE (过时) | 已写 aidb/docs/modules/observability.md | ISSUE-014~018 doc-only |
| `ARCHITECTURE.md` (总审) | ✅ | `backup/aidb/ARCHITECTURE.md`; oldmain `docs/ARCHITECTURE.md`, `MULTI_RAFT_ARCHITECTURE.md`; WiQunTools roadmap 查漏; wiqun-db 与 backup 重复跳过 | 已写 `aidb/ARCHITECTURE.md` | 模块级汇总; ISSUE-014 根文档一行 |
| `DESIGN.md` (总审) | ✅ | `backup/aidb/DESIGN.md`; `oldmain/DESIGN_DECISIONS.md` (原则); `oldmain/ARCHITECTURE.md` §5; CHANGELOG/superpowers (stall/subcompaction); WiQunTools 09–13 查漏 | 已写 `aidb/DESIGN.md` | 模块级; 无新 ISSUE; ISSUE-001/005/014 根文档一行 |
| `README.md` (入口) | ✅ | `backup/aidb/README.md` (主); oldmain `README.md` (查漏, 过时); WiQunTools/wiqun-db 跳过 | 已写 `aidb/README.md` | 模块级; ISSUE-014 一行; 弃 Milestone/:9191/v0.13 |
| `DEPLOYMENT.md` (汇总) | ✅ | `backup/aidb/DEPLOYMENT.md` (主, 多处过时); oldmain `BACKUP_RECOVERY`/`PERFORMANCE_TUNING` (查漏); wiqun-factory `MONITORING` (边界); oldmain FOOLPROOF/USER_GUIDE/monitoring 跳过; wiqun-db 重复跳过; oldmain `monitoring/`/`aidb-admin` 模块级对照 | 已写 `aidb/DEPLOYMENT.md` | 模块级; ISSUE-014/012 根文档一行 |
| `CONTRIBUTING.md` | ✅ | backup/aidb/CONTRIBUTING; oldmain CONTRIBUTING/CICD/DEVELOPMENT (跳过); wiqun-db (acceptance 过时) | 已写 `aidb/CONTRIBUTING.md` | 删覆盖率/WiQunTools; 补测试矩阵与 cluster 入口 |
| `CHANGELOG.md` | ✅ | `backup/aidb/CHANGELOG.md` | 已写 `aidb/CHANGELOG.md` | 保留 0.0.1–0.14.10; [Unreleased] 空 |
| `docs/README.md` (导航) | ✅ | `backup/aidb/README.md` §设计文档; oldmain `INDEX.md` + `DOCUMENT_STRUCTURE.md` (分组查漏); aikv-oldmain `docs/index.md` (形态参考); WiQunTools/wiqun-db 跳过 | 已写 `aidb/docs/README.md` | 纯链接 hub; modules WHEN; A1 无 development.md; C1 README hub 链 |

### aidb 旧文档来源速查

| 来源仓库 | 路径前缀 | 说明 |
|----------|----------|------|
| **backup/aidb/** | 根目录 + `docs/` | 重构后旧稿 (优先参考) |
| aidb-oldmain | `docs/*.md`, `docs/completions/`, `docs/archive/` | 主来源 |
| aidb-oldmain | 根目录 `*.md` (INDEX, TODO, AIKV_INTEGRATION 等) | 按需 |
| wiqun-db | 同 aidb 结构 | 与 aidb 重叠, 二选一即可 |
| WiQunTools | `docs/wiqun-db-inventory/` | 查漏, 不迁入表格 |
| wiqun-factory | `docs/MONITORING.md`, `docs/BUILD.md` | 运维相关 |

---

## aikv

| 新文档章节 | 状态 | 参考的旧文档 | 处理 | 备注 |
|------------|------|--------------|------|------|
| `docs/modules/protocol.md` | ✅ | backup/aikv ARCHITECTURE,DESIGN; WiQunTools 01-resp-tcp; aikv-oldmain src/protocol; wiqun-kv src/protocol | 已写 aikv/docs/modules/protocol.md | 默认 Resp3; 无 ISSUE |
| `docs/modules/server.md` | ✅ | backup/aikv ARCHITECTURE,DESIGN,CHANGELOG; WiQunTools 01-resp-tcp; aikv-oldmain architecture/01-overview + src/server; wiqun-kv src/server (查漏) | 已写 aikv/docs/modules/server.md | listener/connection/config; observability 子模块见 observability.md |
| `docs/modules/storage.md` | ✅ | backup/aikv ARCHITECTURE,DESIGN,CHANGELOG; WiQunTools 02-storage-commands, 06-persistence (查漏 05-lua); aikv-oldmain src/storage/*; wiqun-kv src/storage (查漏) | 已写 aikv/docs/modules/storage.md; oldmain 04-storage.md 已归档 | ISSUE-001/002 open; 加深章 types/memory/adapter/aidb/cluster_adapter |
| `docs/modules/commands-core.md` | ✅ | backup/aikv CHANGELOG,DESIGN; WiQunTools 02-storage-commands; aikv-oldmain 01-commands + src/command/mod.rs; wiqun-kv src/command (查漏) | 已写 aikv/docs/modules/commands-core.md | ISSUE-001 引用; ISSUE-003/004 open; oldmain CommandExecutor→Router |
| `docs/modules/commands-extended.md` | ✅ | backup/aikv README,CHANGELOG,DESIGN; oldmain `01-commands`, `05-lua-scripting`, `src/command/{json,script,server,key}`; WiQunTools 03/04/05/06 (+08 分界); wiqun-kv `src/command` 查漏 | 已写 aikv/docs/modules/commands-extended.md | ISSUE-005~012 |
| `docs/modules/cluster.md` | ✅ | backup/aikv {README,ARCHITECTURE,CHANGELOG,announce plan}; WiQunTools 07-cluster-protocol; oldmain 03-cluster + api/02-cluster (过时段); wiqun-kv cluster (查漏) | 已写 aikv/docs/modules/cluster.md | ISSUE-013/014/016 open; 015/017–019 doc-only; 加深 router/commands/forward/init_cluster |
| `docs/modules/observability.md` | ✅ | backup/aikv superpowers spec + CHANGELOG/DEPLOYMENT; WiQunTools 08; wiqun-factory MONITORING (查漏); oldmain observability/* (过时) | spec 已归档 | ISSUE-020~023; observability-reference.md |
| `ARCHITECTURE.md` (总审) | 待开始 | `backup/aikv/ARCHITECTURE.md` | 已移出 aikv | modules 完成后定稿 |
| `DESIGN.md` (总审) | 待开始 | `backup/aikv/DESIGN.md` | 已移出 aikv | modules 完成后定稿 |
| `README.md` | 待开始 | `backup/aikv/README.md` | 已移出 aikv | 最后修订入口 |
| `DEPLOYMENT.md` | 待开始 | `backup/aikv/DEPLOYMENT.md` | 已移出 aikv | |
| `CHANGELOG.md` | 待开始 | `backup/aikv/CHANGELOG.md` | 已移出 aikv | 保留历史条目, 按需续写 |
| `CONTRIBUTING.md` | 待开始 | `backup/aikv/CONTRIBUTING.md` | 已移出 aikv | |

### aikv 旧文档来源速查

| 来源仓库 | 路径前缀 | 说明 |
|----------|----------|------|
| **backup/aikv/** | 根目录 + `docs/` | 重构后旧稿 (优先参考) |
| aikv-oldmain | `docs/guide/`, `docs/development/` | 主来源 |
| aikv-oldmain | `docs/archive/` | 历史, 按需 |
| wiqun-kv | 同 aikv 结构 | 与 aikv 重叠 |
| WiQunTools | `docs/wiqun-kv-inventory/` | 查漏 |
| wiqun-factory | `docs/superpowers/plans/*wiqun-kv*` | dashboard 等 |

---

## 已从 aidb / aikv 移入 backup 的文档

| 日期 | 原路径 | 现路径 | 说明 |
|------|--------|--------|------|
| 2026-06-16 | `aidb/docs/` | `backup/aidb/docs/` | observability.md + superpowers/ |
| 2026-06-16 | `aikv/docs/` | `backup/aikv/docs/` | superpowers/ |
| 2026-06-16 | `aidb/{README,ARCHITECTURE,DESIGN,DEPLOYMENT,CHANGELOG,CONTRIBUTING}.md` | `backup/aidb/` | 根目录文档整体移出 |
| 2026-06-16 | `aikv/{README,ARCHITECTURE,DESIGN,DEPLOYMENT,CHANGELOG,CONTRIBUTING}.md` | `backup/aikv/` | 根目录文档整体移出 |

---

## 已删除 / 已归档的旧文档 log

按时间倒序追加:

| 日期 | 源仓库 | 旧文件路径 | 对应新章节 | 处理 |
|------|--------|------------|------------|------|
| 2026-06-18 | backup/aikv | `docs/superpowers/specs/2026-06-10-redis-observability-alignment-design.md` | `aikv/docs/modules/observability.md` | 已归档 → `backup/archive/aikv/docs/superpowers/specs/` |
| 2026-06-18 | aidb-oldmain | `docs/monitoring/MONITORING_GUIDE.md` | `docs/modules/observability.md` | 无有效内容跳过 (MetricsServer/Collector 已移除) |
| 2026-06-18 | aidb-oldmain | `docs/monitoring/ADMIN_TOOL_GUIDE.md` §Backup | `docs/modules/backup.md` | 无有效内容跳过 (aidb-admin CLI 已移除) |
| 2026-06-18 | aikv-oldmain | `docs/development/architecture/04-storage.md` | `docs/modules/storage.md` | 已归档 → `backup/archive/aikv-oldmain/docs/development/architecture/04-storage.md` (legacy RDB/AOF, 已过时) |
| | | | | |
