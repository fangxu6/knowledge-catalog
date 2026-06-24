---
type: Query
title: GetOEEData_CUST[0001]
description: OEE 数据查询，供 OEE 报表分析和编辑弹窗读取 OEE_DATA。
resource: CUST_QUERY.GetOEEData_CUST[0001]
tags: [mes, cust-query, oee]
timestamp: 2026-06-23T00:00:00+08:00
---

# Purpose

`GetOEEData_CUST[0001]` 是 OEE 数据读取查询。源码中可见两个调用点：

* `FrmEditOEEData` 读取编辑数据。
* `FrmOEEAnalysis` 读取 OEE 分析数据。

# Known Caller Pattern

```text
QryServiceWithProcess.GetDataByCustQueryID("GetOEEData_CUST", "0001", param)
```

# Expected Outputs

运行时 SQL 不在仓库源码中。本 bundle 只记录当前代码依赖的明显输出列：

| Column | Meaning |
|---|---|
| `QTY` | OEE 汇总实际数量。 |
| `ESTIMATE_QTY` | OEE 汇总预计数量。 |
| `OEE` | OEE 展示列。 |
| `EQP_ID` | 设备维度。 |
| Date / Shift columns | 查询上下文，字段名需以运行时 SQL 为准。 |

# Related Concepts

* [OEE_DATA](../tables/oee-data.md)
* [FrmOEEReport OEE 报表](../reports/oee-report.md)
* [OEE](../metrics/oee.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

