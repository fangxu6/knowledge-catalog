---
type: Table
title: CUST_CARD_INFO
description: Tester 实际板卡登记来源，FUNC00757 中 `TESTER_CARD_DETAIL` 的基础数据。
resource: D:/Workspace/MES/MES_AI
tags: [mes, tester, card, func00757]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`CUST_CARD_INFO` 保存 Tester 实际登记的板卡信息。FUNC00757 使用它生成 `TESTER_CARD_DETAIL`，并与 [ET_PROC_CARD](et-proc-card.md) 产生的 `REQUIRED_PC_CARD` 比较。

# Important Fields

| Field | Meaning |
|---|---|
| `AUXILIARY_EQP_ID` | Tester 设备编号。 |
| `AUXILIARY_MODEL_ID` | Tester 型号。 |
| `CARD_TYPE` | 实际登记板卡类型。 |
| `CARD_CNT` | 实际登记板卡数量。 |

# Special Card Rules

特殊板卡可能和基础板卡同步登记：

| Special Card | Base Card |
|---|---|
| `FPVI10_PLUS` | `FPVI` |
| `DIO_PLUS` | `DIO` |
| `DIO_3.0` | `DIO` |

生成 [CARD_GAP](../metrics/card-gap.md) 时，不能把同步登记的基础板卡误判为多余，也不能把特殊板卡统一折算成基础名称输出。

# Relationships

* Generates `TESTER_CARD_DETAIL` in [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md)
* Compared against [ET_PROC_CARD](et-proc-card.md)
* Drives [CARD_GAP](../metrics/card-gap.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

