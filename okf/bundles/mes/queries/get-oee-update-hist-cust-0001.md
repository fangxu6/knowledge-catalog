---
type: Query
title: GetOEEUpdateHist_CUST[0001]
description: FrmOEEReport History 按钮使用的 OEE 更新历史查询。
resource: CUST_QUERY.GetOEEUpdateHist_CUST[0001]
tags: [mes, cust-query, oee, history]
timestamp: 2026-06-23T00:00:00+08:00
---

# Purpose

`GetOEEUpdateHist_CUST[0001]` 用于查询 OEE 更新历史。`FrmOEEReport.BtnHistory_Click` 中通过当前报表条件 `GetCondition()` 作为参数读取历史并绑定到 History grid。

# Caller

```text
FrmOEEReport.BtnHistory_Click
  -> GetCondition()
  -> QryServiceWithProcess.GetDataByCustQueryID("GetOEEUpdateHist_CUST", "0001", param)
```

# Related Concepts

* [OEE_DATA](../tables/oee-data.md)
* [FrmOEEReport OEE 报表](../reports/oee-report.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

