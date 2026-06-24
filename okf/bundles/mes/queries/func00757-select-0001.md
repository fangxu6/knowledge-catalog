---
type: Query
title: FUNC00757_SELECT[0001]
description: FUNC00757 报表的客户化查询，提供 Prober/Tester/产品/板卡基础行，Java 服务再计算 CARD_GAP。
resource: CUST_QUERY.FUNC00757_SELECT[0001]
tags: [mes, cust-query, func00757, mssql]
timestamp: 2026-06-23T00:00:00+08:00
---

# Purpose

`FUNC00757_SELECT[0001]` 查询 Prober 设备、绑定 Tester、当前产品、Tester 实际板卡配置、产品工艺所需板卡。

当前实现中，它负责稳定取数和输出展示列；复杂 [CARD_GAP](../metrics/card-gap.md) 由 Java 后端计算并覆盖。

# Inputs

| Parameter | Required | Meaning |
|---|---:|---|
| `EQP_GROUP_ID` | No | Prober 设备组。 |
| `EQP_ID` | No | Prober 设备编号。 |
| `MODEL_ID` | No | Prober 型号。 |
| `TESTER_MODEL_ID` | No | Tester 型号。 |
| `CARD_TYPE` | No | 板卡类型过滤，多个值用逗号分隔。 |

# Outputs

| Column | Meaning |
|---|---|
| `EQP_ID` | Prober 设备编号。 |
| `MODEL_ID` | Prober 型号。 |
| `EQP_TEMPERATURE` | Prober 温度。 |
| `PROBER_SPECIAL_TYPE` | Prober 特殊类型描述。 |
| `OCR` | Prober OCR。 |
| `CUST_ID` | 当前产品客户。 |
| `PROD_ID` | 当前产品。 |
| `WAFER_SIZE` | 晶圆尺寸。 |
| `PROD_SPECIAL_TYPE` | 产品特殊类型描述。 |
| `PROD_OCR` | 产品标题是否包含 OCR。 |
| `TESTER_EQP_ID` | 绑定 Tester。 |
| `TESTER_TEMPERATURE` | Tester 温度。 |
| `TESTER_SPECIAL_TYPE` | Tester 特殊类型。 |
| `TESTER_OCR` | Tester OCR。 |
| `TESTER_CARD_DETAIL` | Tester 实际板卡展示。 |
| `REQUIRED_PC_CARD` | 当前产品工艺所需板卡。 |
| `CARD_GAP` | Java 后端计算后覆盖的多余板卡。 |

# Source Tables

* [EQP](../tables/eqp.md)
* [ET_PROBER_TESTER](../tables/et-prober-tester.md)
* [EQP_STATE](../tables/eqp-state.md)
* [CUST_CARD_INFO](../tables/cust-card-info.md)
* [PROC_EQP](../tables/proc-eqp.md)
* [ET_PROC_CARD](../tables/et-proc-card.md)

# Key Rules

* `REQUIRED_PC_CARD` 必须保留 `ET_PROC_CARD.CARD_TYPE_DETAIL` 原始名称。
* `REQUIRED_PC_CARD` 应先 `DISTINCT CARD_CNT, CARD_TYPE_DETAIL`，再 `STRING_AGG`。
* `TESTER_CARD_DETAIL` 可使用 `FPVI(...)`、`DIO(...)` 包装展示特殊板卡。
* Java 服务依赖 `TESTER_CARD_DETAIL` 与 `REQUIRED_PC_CARD`，上线前必须确认运行库查询仍返回这两列。

# Caller

```text
Func00757ServiceExt.selectFunc00757Report
  -> QueryService.getDataByCustomQueryID("FUNC00757_SELECT", "0001", param)
```

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

