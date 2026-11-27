# ove-data-change-review

个人数据变更审查 Skill，覆盖PR/MR和已有数据库设计审计：数据库读写、缓存、文件/对象、消息/同步、数据版本和混合客户端。

审查发现分为三个处置级别：

| 级别     | 含义                                                                 |
| -------- | -------------------------------------------------------------------- |
| 强阻塞   | 正确性、适用硬约束、当前及可预见峰值预算或必要确认未满足，合并前解决 |
| 建议优化 | 已证明安全，额外收益不要求本次实现                                   |
| 规模触发 | 远期才出现风险，本次定阈值/指标/负责人/提前量，按计划实施            |

专项包括JSONB默认策略、复杂聚合/数组膨胀、字段/索引规模成本、区分度与键顺序、刷新必要性、事务原子性及新旧读写/上传兼容。

JSONB禁止参与条件及新增相关索引是**个人默认策略**；PostgreSQL本身支持JSONB索引。仓库或用户明确采用其他策略时按适用指令执行并记录依据。

本目录自包含，无其他Skill或专用工具依赖。示例均为虚构，请结合实际项目的规则、规模和证据使用。

## 使用

将完整目录放入所用Agent的个人Skills目录，目录名保持`ove-data-change-review`，不要只复制`SKILL.md`。

```text
使用 $ove-data-change-review 审查当前PR的数据影响，分列强阻塞、建议优化和规模触发，给证据与人工确认缺口。
```

也可用于只读审计：

```text
使用 $ove-data-change-review 审查现有数据模型，先查代码与已有监控，不执行生产扫描或改动。
```

详细内容见[入口](SKILL.md)、[虚构示例](references/examples.md)和[仓库接入](references/integration.md)。Skill不等于平台强制门禁，也不自动批准生产操作或合并。

## 文件

```text
SKILL.md
references/
  database.md
  storage-and-compatibility.md
  examples.md
  report.md
  integration.md
  sources.md
```
