# 旧文档参考索引

> 记录「完善新文档时参考过哪些旧文档、如何处理」.  
> 过程文档, 位于 `AiKv-Workflow/backup/`, 不进入 aidb / aikv.

**图例**: 处理 = `已删源` | `已归档` | `无有效内容跳过`

---

## aidb

| 新文档章节 | 状态 | 参考的旧文档 | 处理 | 备注 |
|------------|------|--------------|------|------|
| `docs/modules/engine.md` | 待开始 | | | |
| `docs/modules/cluster.md` | 待开始 | | | |
| `docs/modules/observability.md` | 待开始 | `backup/aidb/docs/observability.md` | 已移出 aidb | 整理时迁入 aidb |
| `ARCHITECTURE.md` (总审) | 待开始 | | | |
| `DESIGN.md` (总审) | 待开始 | | | |
| `DEPLOYMENT.md` | 待开始 | | | |

### aidb 旧文档来源速查

| 来源仓库 | 路径前缀 | 说明 |
|----------|----------|------|
| aidb-oldmain | `docs/*.md`, `docs/completions/`, `docs/archive/` | 主来源 |
| aidb-oldmain | 根目录 `*.md` (INDEX, TODO, AIKV_INTEGRATION 等) | 按需 |
| wiqun-db | 同 aidb 结构 | 与 aidb 重叠, 二选一即可 |
| WiQunTools | `docs/wiqun-db-inventory/` | 查漏, 不迁入表格 |
| wiqun-factory | `docs/MONITORING.md`, `docs/BUILD.md` | 运维相关 |

---

## aikv

| 新文档章节 | 状态 | 参考的旧文档 | 处理 | 备注 |
|------------|------|--------------|------|------|
| `docs/modules/protocol.md` | 待开始 | | | |
| `docs/modules/storage.md` | 待开始 | | | |
| `docs/modules/commands.md` | 待开始 | | | |
| `docs/modules/cluster.md` | 待开始 | | | |
| `docs/modules/observability.md` | 待开始 | | | |
| `ARCHITECTURE.md` (总审) | 待开始 | | | |
| `DESIGN.md` (总审) | 待开始 | | | |
| `DEPLOYMENT.md` | 待开始 | | | |

### aikv 旧文档来源速查

| 来源仓库 | 路径前缀 | 说明 |
|----------|----------|------|
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

---

## 已删除 / 已归档的旧文档 log

按时间倒序追加:

| 日期 | 源仓库 | 旧文件路径 | 对应新章节 | 处理 |
|------|--------|------------|------------|------|
| | | | | |
