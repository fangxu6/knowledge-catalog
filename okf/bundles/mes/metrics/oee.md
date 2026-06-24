---
type: Metric
title: OEE
description: FrmOEEReport 中基于实际数量与预计数量计算的汇总指标。
resource: D:/Workspace/MES/MES_AI/frontend/MES_UI/Nebula.MOS.Module.Inquiry/Lot/FrmOEEReport.cs
tags: [mes, metric, oee]
timestamp: 2026-06-23T00:00:00+08:00
---

# Definition

在 `FrmOEEReport.SetSummary()` 中，OEE 汇总公式为：

```text
ROUNDDOWN(SUM(QTY) / SUM(ESTIMATE_QTY) * 100, 2)
```

报表显示格式为：

```text
平均 = {0}%
```

# Inputs

| Input | Meaning |
|---|---|
| `QTY` | 实际数量。 |
| `ESTIMATE_QTY` | 预计数量。 |

# Relationships

* Data object: [OEE_DATA](../tables/oee-data.md)
* Report surface: [FrmOEEReport OEE 报表](../reports/oee-report.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

