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

**起步**: ~~P0~~ ✅; ~~A2 P1~~ ✅; ~~A4 doc-only~~ ✅; ~~A3 P2/P3~~ ✅; ~~B2-v0 testviz~~ ✅ → **下一**: 阶段 2 并行 **C1** monitor / (可选) **B2-v0.1**.

---

## P1 — Redis / 集群语义与运维误导

| 序 | 仓库 | ID | 标题 | 备注 |
|----|------|-----|------|------|
| 5 | aikv | ISSUE-001 | MemoryEngine mget 对非 String 静默 None | **closed** |
| 6 | aikv | ISSUE-006 | MIGRATE KEYS 忽略 COPY | **closed** |
| 7 | aikv | ISSUE-013 | CLUSTER INFO 恒 `cluster_state:ok` | **closed** |
| 8 | aikv | ISSUE-016 | CLUSTER RESET 未实现 | **closed** (doc-only) |
| 9 | aikv | ISSUE-012 | EVAL KeyLock 无超时 | **closed** |

---

## P2 — 功能缺口 / 兼容 (按需求排)

| 仓库 | ID | 标题 |
|------|-----|------|
| aikv | ISSUE-003 | GETRANGE/SETRANGE 未实现 | **closed** |
| aikv | ISSUE-004 | cluster_route 预留 MSETNX 未注册 | **closed** (doc-only) |
| aikv | ISSUE-009 | Lua redis.call JSON.MGET 未实现 | **closed** |
| aikv | ISSUE-010 | MIGRATE 无 AUTH2 | **closed** |
| aikv | ISSUE-014 | GossipState 未接入 CLUSTER NODES | **closed** |
| aikv | ISSUE-017 | CLUSTER REPLICATE 仅本地元数据 | **closed** (doc-only) |
| aikv | ISSUE-018 | CLUSTER FAILOVER 仅 FORCE/TAKEOVER | **closed** (doc-only) |
| aikv | ISSUE-019 | SET-CONFIG-EPOCH / COUNT-FAILURE-REPORTS stub | **closed** (doc-only) |

---

## P3 — 可观测性 / 体验 (不阻塞核心)

| 仓库 | ID | 标题 | 当前状态 |
|------|-----|------|----------|
| aikv | ISSUE-020 | `blocked_clients` 无写入点 | **closed** |
| aikv | ISSUE-005 | BlockingRegistry evict_expired 无 caller | **closed** |
| aikv | ISSUE-021 | refresh_runtime_metrics 仅 monitoring tick | **closed** (doc-only) |
| aikv | ISSUE-022 | metrics refresh 15s vs spec 1s | **closed** (doc-only) |
| aikv | ISSUE-023 | Slowlog 默认 100ms vs Redis 10ms | **closed** (doc-only) |

aidb **ISSUE-006–018** 多为 **closed/doc-only**; 除 P0 的 **005** 外无 open 代码债.

---

## doc-only 批量 (aikv) — ✅ 2026-06-22

已 `closed (doc-only)`: ISSUE-007, 008, 011, 015, 017–019, 021–023.

仍 open: (无 — A3 P3 代码债已清)

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
| 2026-06-23 | **B2-v0** testviz 最小可用 (`AiFactory/testviz/`); 下一 C1 / B2-v0.1 |
| 2026-06-23 | **A3 ISSUE-020** closed (`blocked_clients` 阻塞计数); 线路 A P3 代码债已清; 下一 B2-v0/C1 |
| 2026-06-23 | **A3 ISSUE-005** closed (BlockingRegistry 后台 evict); 下一 A3 P3 020 或 B2-v0/C1 |
| 2026-06-22 | **A3 ISSUE-010** closed (MIGRATE AUTH2); 下一 A3 P2 017 或 B2-v0/C1 |
| 2026-06-22 | **A3 ISSUE-009** closed (JSON.MGET 顶层 + Lua); 下一 A3 P2 010 或 B2-v0/C1 |
| 2026-06-22 | **A3 ISSUE-004** closed doc-only (MSETNX 不实现; 移除 cluster_route dead branch); 下一 A3 P2 或 B2-v0/C1 |
| 2026-06-22 | **A3 ISSUE-014** closed (移除 GossipState; NODES link-state); 下一 A3 P2 或 B2-v0/C1 |
| 2026-06-22 | **A4 doc-only**: aikv 007/008/011/015/017–019/021–023 closed; 下一 A3 ISSUE-014 或 P2 |
| 2026-06-22 | **A2 P1 全部关闭** (序 5–9); 下一: A4 doc-only 或 A3 ISSUE-014 |
| 2026-06-22 | aikv ISSUE-012 closed (EVAL KeyLock 30s 锁等待超时); A2 P1 序 9 完成 |
| 2026-06-22 | aikv ISSUE-001 closed (MGET Redis 7 wrong-type → nil, 双引擎统一); 下一 P1: 012 |
| 2026-06-22 | aikv ISSUE-016 closed doc-only (CLUSTER RESET ERR + 排障); 下一 P1: 001 或 012 |
| 2026-06-22 | aikv ISSUE-013 closed (CLUSTER INFO cluster_state fail); 下一 P1: 001 或 016 |
| 2026-06-22 | aidb ISSUE-001/002 closed; B1.2 WAL 回归测模板; 下一 P0: aikv 002 或 aidb 005 |
| 2026-06-16 | 对齐 PLAN-dev v1 三线路引用 |
| 2026-06-18 | 初版: 文档整理 Step 3 验收后 ISSUES 开发优先级 |
