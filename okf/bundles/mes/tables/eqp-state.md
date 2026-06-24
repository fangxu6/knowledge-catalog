---
type: Table
title: EQP_STATE
description: 设备运行态表，FUNC00757 通过它获取 Prober 当前产品 `PROD_ID`。
resource: D:/Workspace/MES/MES_AI
tags: [mes, runtime, equipment, product]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`EQP_STATE` 是运行态数据，表示设备当前状态。FUNC00757 通过 `EQP_STATE.EQP_ID = EQP.EQP_ID` 找到 Prober 当前产品 `PROD_ID`，再连接产品主数据获取客户、晶圆尺寸、产品特殊类型和 OCR 判断。

# Important Fields

| Field | Meaning |
|---|---|
| `EQP_ID` | 设备编号，连接 [EQP](eqp.md)。 |
| `PROD_ID` | 当前设备上的产品。 |
| `RECIPE_ID` | 当前设备/产品运行相关 Recipe，具体使用依场景而定。 |
| `EVENT_*` | 运行态事件和审计字段。 |

# Boundary

不要用 [PROC_EQP](proc-eqp.md) 替代 `EQP_STATE` 回答当前运行态问题。`PROC_EQP` 是主数据配置，`EQP_STATE` 才是设备当前状态侧的数据。

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

