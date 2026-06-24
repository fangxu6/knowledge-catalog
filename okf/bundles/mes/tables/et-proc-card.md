---
type: Table
title: ET_PROC_CARD
description: 工艺设备所需板卡配置表，FUNC00757 中 `REQUIRED_PC_CARD` 的来源。
resource: D:/Workspace/MES/MES_AI
tags: [mes, mdm, cp, card, func00757]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`ET_PROC_CARD` 定义某个工艺设备配置需要哪些板卡、每种几张。它是 [FUNC00757](../reports/func00757.md) 中产品所需板卡字段 `REQUIRED_PC_CARD` 的来源。

# Important Fields

| Field | Meaning |
|---|---|
| `PROC_RULE_ID` | 工艺规则标识，和 [PROC_EQP](proc-eqp.md) 对齐。 |
| `EQP_ID` / `PROC_EQP_ID` | 与工艺设备配置关联的设备键，具体字段名需按现场 SQL 确认。 |
| `CARD_CNT` | 所需板卡数量。 |
| `CARD_TYPE_DETAIL` | 所需板卡类型，必须保留原始类型，例如 `FPVI10_PLUS`、`DIO_PLUS`、`DIO_3.0`。 |

# Query Semantics

在 `FUNC00757_SELECT[0001]` 中，所需板卡按以下路径生成：

```text
PROD_ID -> PRP -> PROC_RULE -> PROC_EQP -> ET_PROC_CARD
```

`REQUIRED_PC_CARD` 必须先按 `CARD_CNT + CARD_TYPE_DETAIL` 去重，再聚合成展示字符串，否则会因 `PROC_RULE x PROC_EQP` 展开导致重复板卡。

# Relationships

* Used by [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md)
* Compared with [CUST_CARD_INFO](cust-card-info.md)
* Feeds [CARD_GAP](../metrics/card-gap.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

