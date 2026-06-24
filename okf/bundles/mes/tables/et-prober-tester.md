---
type: Table
title: ET_PROBER_TESTER
description: Prober 与 Tester 的绑定关系表，FUNC00757 通过它找到 Prober 当前关联的 Tester。
resource: D:/Workspace/MES/MES_AI
tags: [mes, cp, prober, tester]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`ET_PROBER_TESTER` 把 Prober 设备与 Tester 设备关联起来。FUNC00757 查询从 [EQP](eqp.md) 的 Prober 出发，通过本表得到 `TESTER_EQP_ID`，再回到 [EQP](eqp.md) 读取 Tester 的温度、特殊类型和 OCR。

# Important Fields

| Field | Meaning |
|---|---|
| `PROBER_EQP_ID` | Prober 设备编号。 |
| `TESTER_EQP_ID` | Tester 设备编号。 |

# Relationships

* Source Prober: [EQP](eqp.md)
* Target Tester: [EQP](eqp.md)
* Tester cards: [CUST_CARD_INFO](cust-card-info.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

