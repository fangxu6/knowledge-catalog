---
type: Table
title: EQP
description: 设备主档，FUNC00757 中同时作为 Prober 与 Tester 设备信息来源。
resource: D:/Workspace/MES/MES_AI
tags: [mes, mdm, equipment]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`EQP` 是设备主档。FUNC00757 中主查询以 Prober 设备为主表，同时通过 [ET_PROBER_TESTER](et-prober-tester.md) 关联 Tester 设备，再回到 `EQP` 读取 Tester 主数据。

# Important Fields

| Field | Meaning |
|---|---|
| `EQP_ID` | 设备编号。 |
| `MODEL_ID` | 设备型号。 |
| `DET_EQP_TYPE` | 明细设备类型；FUNC00757 过滤 `Prober`。 |
| `VIRTUAL_EQP_YN` | 是否虚拟设备；FUNC00757 排除 `Y`。 |
| `EQP_GRP_ID` | 设备组过滤条件。 |
| `EQP_TEMPERATURE` | 设备温度属性。 |
| `SPECIAL_TYPE` | 特殊类型代码，通过 `ENUM_VAL` 转描述。 |
| `OCR` | OCR 相关配置。 |

# Relationships

* Prober current product comes from [EQP_STATE](eqp-state.md)
* Prober to Tester binding comes from [ET_PROBER_TESTER](et-prober-tester.md)
* Tester actual cards come from [CUST_CARD_INFO](cust-card-info.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

