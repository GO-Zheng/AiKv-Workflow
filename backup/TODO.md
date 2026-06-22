# ISSUES 开发优先级

> 过程文档, 位于 `AiKv-Workflow/backup/`. 条目详情在各产品仓库 `ISSUES.md`; 本文只记录 **处理顺序与起步建议**.  
> **总计划**: 见 [PLAN-dev.md](PLAN-dev.md) (**v1 实施计划** — 线路 A ISSUES / B 测试 / C monitor).

**详情源**:

| 仓库 | 文件 |
|------|------|
| aidb | [`aidb/ISSUES.md`](../../aidb/ISSUES.md) |
| aikv | [`aikv/ISSUES.md`](../../aikv/ISSUES.md) |

**状态图例** (与各仓库 ISSUES 一致): `open` | `confirmed-bug` | `doc-only` | `closed`

---

## 处理流程 (每条 open 条目)

1. **复现** — 按条目 `相关 src` 写最小测试或 `redis-cli`/单元测试; 区分 bug vs intentional
2. **定状态** — `open` → `confirmed-bug` / `doc-only` / `closed`
3. **开分支修** — 建议一 issue 一分支, 或同域小批 (如 cluster 多条)
4. **收尾** — 代码 + 测试; 更新对应仓库 `ISSUES.md`; module「待核实」删或改一句; 必要时 `CHANGELOG.md`

**doc-only 条目**: 默认 **不修代码**; 文档已描述即可 `closed (doc-only)`, 除非主动决定改默认行为.

---

## P0 — 数据 / 生产路径 (先核实)

可能伤数据、恢复或生产配置; **建议第一条开发线**.

| 序 | 仓库 | ID | 标题 | 状态 | 相关 src |
|----|------|-----|------|------|----------|
| 1 | aidb | ISSUE-001 | WriteBatch 可能跨 WAL 文件 | **closed** | `engine/db/inner.rs`, `engine/wal/manager.rs` |
| 2 | aidb | ISSUE-002 | 大 WriteBatch 与 max_wal_size 轮转交互 | **closed** (同 001) | 同上 |
| 3 | aidb | ISSUE-005 | 数据 Group apply 仍逐 entry 写 last_applied | **closed** | `cluster/storage/apply.rs` |
| 4 | aikv | ISSUE-002 | AiDbEngine::open 固定 `Options::for_testing()` | **closed** | `storage/aidb.rs`, `storage/aidb_options.rs` |

**起步**: ~~aidb 001 + 002~~ ✅; ~~aikv 002~~ ✅; ~~aidb 005~~ ✅; ~~A0~~ ✅; ~~aikv 006~~ ✅ → **下一: A2 P1 · aikv 001 或 013**.

---

## P1 — Redis / 集群语义与运维误导

| 序 | 仓库 | ID | 标题 | 备注 |
|----|------|-----|------|------|
| 5 | aikv | ISSUE-001 | MemoryEngine mget 对非 String 静默 None | memory vs aidb 语义不一致 |
| 6 | aikv | ISSUE-006 | MIGRATE KEYS 忽略 COPY | **closed** |
| 7 | aikv | ISSUE-013 | CLUSTER INFO 恒 `cluster_state:ok` | 排障可能误判 |
| 8 | aikv | ISSUE-016 | CLUSTER RESET 未实现 | 运维链断 |
| 9 | aikv | ISSUE-012 | EVAL KeyLock 无超时 | 同 key 死锁风险 |

---

## P2 — 功能缺口 / 兼容 (按需求排)

| 仓库 | ID | 标题 |
|------|-----|------|
| aikv | ISSUE-003 | GETRANGE/SETRANGE 未实现 |
| aikv | ISSUE-004 | cluster_route 预留 MSETNX 未注册 |
| aikv | ISSUE-009 | Lua redis.call JSON.MGET 未实现 |
| aikv | ISSUE-010 | MIGRATE 无 AUTH2 |
| aikv | ISSUE-014 | GossipState 未接入 CLUSTER NODES |
| aikv | ISSUE-017 | CLUSTER REPLICATE 仅本地元数据 |
| aikv | ISSUE-018 | CLUSTER FAILOVER 仅 FORCE/TAKEOVER |
| aikv | ISSUE-019 | SET-CONFIG-EPOCH / COUNT-FAILURE-REPORTS stub |

---

## P3 — 可观测性 / 体验 (不阻塞核心)

| 仓库 | ID | 标题 | 当前状态 |
|------|-----|------|----------|
| aikv | ISSUE-020 | `blocked_clients` 无写入点 | open |
| aikv | ISSUE-005 | BlockingRegistry evict_expired 无 caller | open |
| aikv | ISSUE-021 | refresh_runtime_metrics 仅 monitoring tick | doc-only |
| aikv | ISSUE-022 | metrics refresh 15s vs spec 1s | doc-only |
| aikv | ISSUE-023 | Slowlog 默认 100ms vs Redis 10ms | doc-only |

aidb **ISSUE-006–018** 多为 **closed/doc-only**; 除 P0 的 **005** 外无 open 代码债.

---

## doc-only 批量 (aikv, 可不写代码)

以下文档已覆盖或 intentional; 有空可批量 `closed (doc-only)`:

ISSUE-007, 008, 011, 015, 017–019 (部分 P2 已列), 021–023.

aikv ISSUE-015 (METARAFT 子命令移除) — doc-only, 链 aidb cluster.

---

## 推荐第一条开发线

```text
1. aidb: ISSUE-001 + 002  (WAL 测试 → 修/关)
2. aikv: ISSUE-002        (生产 Options / CLI)  ✅
3. aikv: ISSUE-006        (MIGRATE COPY, 小 patch)
4. 集群域: 013 / 016 / 014 (常跑 cluster 时再排)
5. doc-only 扫一遍 → closed
```

---

## 与文档整理 / 删旧仓

- **Step 3 主观验收**、**Step 4 删旧仓库** 不依赖 ISSUES 全清
- 修代码以 **当前 aidb/aikv + 测试** 为准; oldmain 仅 ISSUES 条目内对照参考
- 删仓前若需保留 oldmain 对照, 见 `backup/archive/` 或条目内已记录的 `oldmain 代码` 路径

---

## 变更 log

| 日期 | 说明 |
|------|------|
| 2026-06-22 | aikv ISSUE-006 closed (MIGRATE KEYS + COPY); 下一 P1: 001 或 013 |
| 2026-06-22 | aidb ISSUE-001/002 closed; B1.2 WAL 回归测模板; 下一 P0: aikv 002 或 aidb 005 |
| 2026-06-16 | 对齐 PLAN-dev v1 三线路引用 |
| 2026-06-18 | 初版: 文档整理 Step 3 验收后 ISSUES 开发优先级 |
