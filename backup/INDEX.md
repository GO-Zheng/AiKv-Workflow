# 旧文档参考索引

> 记录「完善新文档时参考过哪些旧文档、如何处理」.  
> 过程文档, 位于 `AiKv-Workflow/backup/`, 不进入 aidb / aikv.  
> 待核实 / 可能 bug 详情见 [ISSUES.md](ISSUES.md); module 内一行引用即可.

**图例**: 处理 = `已删源` | `已归档` | `无有效内容跳过`

---

## aidb

| 新文档章节 | 状态 | 参考的旧文档 | 处理 | 备注 |
|------------|------|--------------|------|------|
| `docs/modules/engine.md` | 待开始 | | | `engine/{wal,memtable,db}` |
| `docs/modules/engine-storage.md` | 待开始 | | | `engine/{sstable,compaction,filter,cache,checkpoint}` |
| `docs/modules/cluster.md` | 待开始 | | | `cluster/*` |
| `docs/modules/backup.md` | 待开始 | | | `backup/*` |
| `docs/modules/observability.md` | 待开始 | `backup/aidb/docs/observability.md` | 已移出 aidb | `metrics.rs` + monitoring |
| `ARCHITECTURE.md` (总审) | 待开始 | `backup/aidb/ARCHITECTURE.md` | 已移出 aidb | modules 完成后定稿 |
| `DESIGN.md` (总审) | 待开始 | `backup/aidb/DESIGN.md` | 已移出 aidb | modules 完成后定稿 |
| `README.md` | 待开始 | `backup/aidb/README.md` | 已移出 aidb | 最后修订入口 |
| `DEPLOYMENT.md` | 待开始 | `backup/aidb/DEPLOYMENT.md` | 已移出 aidb | |
| `CHANGELOG.md` | 待开始 | `backup/aidb/CHANGELOG.md` | 已移出 aidb | 保留历史条目, 按需续写 |
| `CONTRIBUTING.md` | 待开始 | `backup/aidb/CONTRIBUTING.md` | 已移出 aidb | |

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
| `docs/modules/protocol.md` | 待开始 | | | `protocol/*` |
| `docs/modules/server.md` | 待开始 | | | `server/*` |
| `docs/modules/storage.md` | 待开始 | | | `storage/*` |
| `docs/modules/commands-core.md` | 待开始 | | | string/hash/list/set/zset/key/db + router |
| `docs/modules/commands-extended.md` | 待开始 | | | json/lua/blocking/migrate/persistence/server |
| `docs/modules/cluster.md` | 待开始 | | | `cluster/*` + cluster_commands |
| `docs/modules/observability.md` | 待开始 | `backup/aikv/docs/superpowers/*observability*` | | slowlog/latency/info/metrics |
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
| | | | | |
