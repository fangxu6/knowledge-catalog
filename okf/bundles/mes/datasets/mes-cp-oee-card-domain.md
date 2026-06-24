---
type: Knowledge Domain
title: MES CP OEE Card Domain
description: MES 中围绕 CP 工艺设备配置、OEE 报表和 FUNC00757 板卡差额的本地 OKF 知识域。
resource: D:/Workspace/MES/MES_AI
tags: [mes, cp, oee, card-gap, okf]
timestamp: 2026-06-23T00:00:00+08:00
---

# Scope

这个知识域只覆盖第一版可验证对象，不试图穷尽整个 MES：

* MDM 主数据配置中的 [PROC_EQP](../tables/proc-eqp.md) 与 [ET_PROC_CARD](../tables/et-proc-card.md)。
* MES 运行态中的 [EQP_STATE](../tables/eqp-state.md) 与 [OEE_DATA](../tables/oee-data.md)。
* 设备主档和绑定关系：[EQP](../tables/eqp.md)、[ET_PROBER_TESTER](../tables/et-prober-tester.md)。
* Tester 实际板卡来源：[CUST_CARD_INFO](../tables/cust-card-info.md)。
* 两个报表面：[FUNC00757](../reports/func00757.md)、[FrmOEEReport](../reports/oee-report.md)。

# Design Notes

该 bundle 刻意保留“配置”和“运行态”的边界：

* [PROC_EQP](../tables/proc-eqp.md) 与 [ET_PROC_CARD](../tables/et-proc-card.md) 是工艺配置口径，不等同于现场设备当前挂载状态。
* [EQP_STATE](../tables/eqp-state.md) 提供设备当前产品，FUNC00757 用它把 Prober 设备关联到产品。
* [CUST_CARD_INFO](../tables/cust-card-info.md) 是 Tester 实际板卡登记，不能直接等同于产品工艺所需板卡。
* [CARD_GAP](../metrics/card-gap.md) 只表达实际多出的板卡，不表达缺少的板卡。

# Agent Reading Path

1. 先读本文件确认范围。
2. 如果要解释 FUNC00757，读 [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md) 和 [CARD_GAP](../metrics/card-gap.md)。
3. 如果要解释 OEE 编辑，读 [FrmOEEReport OEE 报表](../reports/oee-report.md) 和 [OEE_DATA](../tables/oee-data.md)。
4. 如果要追工艺配置，读 [PROC_EQP](../tables/proc-eqp.md) 与 [ET_PROC_CARD](../tables/et-proc-card.md)。

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

