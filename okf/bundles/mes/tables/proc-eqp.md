---
type: Table
title: PROC_EQP
description: 工艺规则下的设备配置表，定义产品工艺、工站与可用设备/设备模型/CP 参数之间的关系。
resource: D:/Workspace/MES/MES_AI
tags: [mes, mdm, process, equipment, cp]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`PROC_EQP` 属于 MDM 主数据配置口径。它描述工艺规则允许或配置的设备，不是 MES 运行态当前设备挂载结果。

在本知识域中，它是以下链路的中间锚点：

* [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md) 中的 `PRP -> PROC_RULE -> PROC_EQP -> ET_PROC_CARD`。
* [ET_PROC_CARD](et-proc-card.md) 的板卡需求归属。
* CP 改机、TrackIn、ReplaceEQP 等运行流程中的 `PROC_EQP_ID` 参数来源。
* PRP release 复制配置时，复制 `PROC_EQP` 后触发 OeeTime 补齐。

# Important Fields

| Field | Meaning |
|---|---|
| `PROC_RULE_ID` | 工艺规则主键，连接 `PROC_RULE` 与本表。 |
| `PROC_EQP_ID` | 工艺配置维度的设备键，不是现场设备主键。 |
| `PRP_ID` | 产品工艺或产品路线标识。 |
| `FLOW_ID` | 流程标识。 |
| `OPER_ID` | 工站标识。 |
| `EQP_ID` | 设备或设备模型相关标识，具体语义需结合上下文。 |
| `PROBER_GRP` | CP 场景中用于针卡/Prober 组匹配的配置。 |
| `DEVICE` | CP 设备相关配置项。 |
| `DUT` | CP DUT 配置项。 |
| `DEFAULT_YN` | 默认设备配置标识。 |

# Relationships

* Required card configuration: [ET_PROC_CARD](et-proc-card.md)
* Product and process rule source in FUNC00757: [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md)
* Runtime device state should not be inferred from this table alone: [EQP_STATE](eqp-state.md)
* OEE release copy side effect: [OEE_DATA](oee-data.md)

# Notes

`PROC_EQP_ID` 是高风险歧义字段。它经常被前端页面和后端接口传递，但它不是 `EQP.EQP_ID`。回答“当前挂了什么设备”时，不能只看 `PROC_EQP`，还需要结合运行态表和业务入口。

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

