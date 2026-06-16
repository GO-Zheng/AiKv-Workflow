# AiDb / AiKv 文档整理方案

> 过程文档, 存放于 `AiKv-Workflow/backup/` (本仓库, 有 git 记录). 不进入 aidb / aikv 仓库.

**日期**: 2026-06-16  
**状态**: 已确认

---

## 目标

为 **个人继续开发** 整理 aidb 与 aikv 文档. 最终只保留 aidb / aikv 两个仓库; 其它仓库 (aidb-oldmain, aikv-oldmain, wiqun-db, wiqun-kv, wiqun-factory, WiQunTools) 在验收后删除.

## 原则

1. **aidb / aikv 只放当前有效文档** — 面向「现在代码怎么用、怎么组织」, 不记录迁移历史.
2. **所有整理过程放在 AiKv-Workflow/backup/** — 索引、进度、旧文档归档、本方案 (弃用的 AiKv-Workflow 仓库承载, 便于版本管理).
3. **按章节渐进** — 先定文档骨架, 再逐章完善; 完善一章, 消化相关旧文档, 清掉源侧干扰.
4. **旧文档不迁入 inventory 表格** — WiQunTools 等功能清单仅作查漏参考, 不复制进项目.
5. **其它仓库文档整理期间只读不改** — 源侧文件可在消化后直接删除.

## 不做的事

- 不在 aidb / aikv 中建立 `refactoring/`、`module-map`、迁移对照表
- 不整体迁入 WiQunTools inventory
- 不在项目仓库维护整理进度表

---

## 工作流

```
Step 0  确定 aidb / aikv 文档骨架 (见下文「目标文档结构」)
        初始化 backup/INDEX.md + backup/PROGRESS.md

Step 1  按 PROGRESS 顺序选一个章节
        1. 以新代码为准, 编写 / 修订 aidb 或 aikv 对应文档
        2. 在旧仓库搜索相关文档, 对比代码, 提取仍准确的内容合并进新文档
        3. 在 backup/INDEX.md 记录参考来源与处理结论
        4. 在 backup/PROGRESS.md 标记 ✅
        5. 源仓库中已消化的旧文档: 移入 backup/archive/ 或直接删除

Step 2  重复 Step 1, 直至 PROGRESS 全部 ✅

Step 3  总审 aidb / aikv 顶层 ARCHITECTURE.md、DESIGN.md
        主观验收: 能否仅凭新文档定位任意功能的代码位置

Step 4  删除 aidb-oldmain、aikv-oldmain、wiqun-db、wiqun-kv、wiqun-factory、WiQunTools
        AiKv-Workflow/backup/ 保留 (git 历史); archive/ 内旧文档副本可按需清理
```

### 每章固定三步

| 步骤 | 动作 |
|------|------|
| 写 | 新代码 → aidb / aikv 文档 |
| 查 | 旧文档 → 对比代码 → 合并有效内容 |
| 清 | backup 记一笔 → 源侧旧文档移除 |

---

## 旧文档来源 (只读参考)

| 仓库 | 对应产品 | 用途 |
|------|----------|------|
| aidb-oldmain | aidb | 实现细节、集群、运维类旧文档 |
| aikv-oldmain | aikv | guide、development、architecture 旧文档 |
| wiqun-db | aidb (重构中间态) | 与 aidb 文档重叠, 按需参考 |
| wiqun-kv | aikv (重构中间态) | 与 aikv 文档重叠, 按需参考 |
| WiQunTools | 两者 | inventory 查漏; project-design 理解重构意图 |
| wiqun-factory | 部署/监控 | 监控、构建说明, 按需提炼进 DEPLOYMENT / observability |

命名映射: **wiqun-db = aidb**, **wiqun-kv = aikv**.

---

## 目标文档结构

### aidb

```
aidb/
├── README.md
├── AGENTS.md
├── ARCHITECTURE.md          # 系统级架构, 各章完成后总审
├── DESIGN.md                # 设计决策, 各章完成后总审
├── DEPLOYMENT.md
├── CHANGELOG.md
├── CONTRIBUTING.md
└── docs/
    ├── README.md            # 文档导航 (纯链接, 无迁移信息)
    ├── development.md       # 本地构建、测试矩阵、常见开发任务
    ├── modules/
    │   ├── engine.md        # WAL, MemTable, SSTable, Compaction, Filter, Cache, DB API
    │   ├── cluster.md       # MetaRaft, MultiRaft, Router, Slot 迁移, gRPC
    │   └── observability.md # metrics, tracing, 慢查询 (参考 backup/aidb/docs/observability.md)
    └── (无 superpowers; 已移至 AiKv-Workflow/backup/aidb/docs/superpowers/)
```

### aikv

```
aikv/
├── README.md
├── AGENTS.md
├── ARCHITECTURE.md
├── DESIGN.md
├── DEPLOYMENT.md
├── CHANGELOG.md
├── CONTRIBUTING.md
└── docs/
    ├── README.md
    ├── development.md
    ├── modules/
    │   ├── protocol.md      # RESP, TCP, pipeline
    │   ├── commands.md      # CommandRouter, 命令分类与扩展方式
    │   ├── storage.md       # KvStorage, MemoryEngine, AiDbEngine, 编码
    │   ├── cluster.md       # Cluster 协议, MOVED/ASK, slot 迁移
    │   └── observability.md # metrics, slowlog, latency, INFO 字段
    └── (无 superpowers; 已移至 AiKv-Workflow/backup/aikv/docs/superpowers/)
```

### Step 0 待创建 / 待迁移文件

| 仓库 | 动作 |
|------|------|
| aidb | 新建 `docs/README.md`, `docs/development.md`, `docs/modules/{engine,cluster}.md` |
| aidb | 迁移 `backup/aidb/docs/observability.md` → `docs/modules/observability.md` |
| aikv | 新建 `docs/README.md`, `docs/development.md`, `docs/modules/*.md` (5 个) |

新建文件可先写标题 + 「待完善」占位, 正文在 Step 1 按章填充.

---

## 章节推进顺序

| 顺序 | aidb 章节 | aikv 章节 | 说明 |
|------|-----------|-----------|------|
| 1 | `modules/engine.md` | `modules/protocol.md` | 底层, 其它章依赖 |
| 2 | `modules/cluster.md` | `modules/storage.md` | 依赖 engine / protocol |
| 3 | `modules/observability.md` | `modules/commands.md` | 相对独立 |
| 4 | 总审 ARCHITECTURE + DESIGN | `modules/cluster.md` | 需前几章输入 |
| 5 | — | `modules/observability.md` | 最后 |
| 6 | 总审 ARCHITECTURE + DESIGN | 总审 ARCHITECTURE + DESIGN | 收尾 |

---

## AiKv-Workflow/backup/ 目录结构

```
AiKv-Workflow/
└── backup/
    ├── design.md
    ├── INDEX.md
    ├── PROGRESS.md
    ├── aidb/docs/         # 自 aidb 仓库移出 (observability + superpowers)
    ├── aikv/docs/         # 自 aikv 仓库移出 (superpowers)
    └── archive/           # 从其它旧仓库移出的文档
        ├── aidb-oldmain/
        ├── aikv-oldmain/
        └── ...
```

---

## 验收标准 (Step 3)

- [ ] aidb / aikv 的 `docs/README.md` 导航完整, 链接有效
- [ ] 每个 `docs/modules/*.md` 与当前 `src/` 结构一致, 路径准确
- [ ] 能仅凭 aidb / aikv 文档定位任意功能的代码入口 (主观)
- [ ] wiqun-factory 中仍需要的部署 / 监控说明已提炼进 DEPLOYMENT 或 observability 章节
- [ ] PROGRESS.md 全部 ✅
- [ ] 旧仓库可安全删除

---

## 对比深度 (B 档)

对比发生在 **每章 Step 1** 内, 不单独产出迁移文档:

- 确认新文档描述的模块边界、关键 trait/API 与代码一致
- 从旧文档提取仍准确的实现细节 (格式、流程、配置项)
- 差异与重构原因直接写入新文档正文 (如 DESIGN 或 module 内「设计说明」小节), 不另建对照表
