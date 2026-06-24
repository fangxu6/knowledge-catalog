---
type: Table
title: OEE_DATA
description: OEE 报表数据对象，被 FrmOEEReport 和 OEE 编辑弹窗读取、编辑、汇总。
resource: D:/Workspace/MES/MES_AI
tags: [mes, oee, report, runtime]
timestamp: 2026-06-23T00:00:00+08:00
---

# Role

`OEE_DATA` 是 OEE 报表和编辑弹窗使用的数据对象。`FrmOEEReport` 打开编辑窗体时设置：

```text
form.GridId = "OEE_DATA"
```

编辑弹窗通过 `UPDATE_OEE_DATA` 服务保存，并通过 `GetOEEData_CUST[0001]` 查询数据。

# Important Fields

| Field | Meaning |
|---|---|
| `QTY` | 实际数量，参与 OEE 汇总。 |
| `ESTIMATE_QTY` | 预计数量，参与 OEE 汇总。 |
| `OEE` | 报表展示指标，汇总口径见 [OEE](../metrics/oee.md)。 |
| `DATE` / `SHIFT` | OEE 查询和编辑上下文，实际字段名需以运行时查询为准。 |
| `EQP_ID` | 设备维度。 |
| `EVENT_*` | 更新历史和审计字段。 |

# Relationships

* Display report: [FrmOEEReport OEE 报表](../reports/oee-report.md)
* Data query: [GetOEEData_CUST[0001]](../queries/get-oee-data-cust-0001.md)
* History query: [GetOEEUpdateHist_CUST[0001]](../queries/get-oee-update-hist-cust-0001.md)
* Summary metric: [OEE](../metrics/oee.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

