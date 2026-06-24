---
type: Report
title: FrmOEEReport OEE 报表
description: MES_UI 中用于 OEE 查询、编辑、历史查看和汇总的 WinForms 报表窗体。
resource: D:/Workspace/MES/MES_AI/frontend/MES_UI/Nebula.MOS.Module.Inquiry/Lot/FrmOEEReport.cs
tags: [mes, oee, winforms, report]
timestamp: 2026-06-23T00:00:00+08:00
---

# Purpose

`FrmOEEReport` 是 WinForms 报表窗体，继承通用报表基类。它负责展示 OEE 数据、打开编辑弹窗、查看历史，并在查询后计算汇总行。

# Runtime Path

```text
FrmOEEReport
  -> AfterSearch
  -> SetSummary()
  -> AddSummary("SUM1", "QTY", "SUM([QTY])")
  -> AddSummary("SUM2", "ESTIMATE_QTY", "SUM([ESTIMATE_QTY])")
  -> AddSummary("OEE", "OEE", "ROUNDDOWN(SUM([QTY]) / SUM([ESTIMATE_QTY]) * 100, 2)")
```

编辑路径：

```text
BtnEdit_Click
  -> new FrmEditOEEData(date, shift)
  -> form.GridId = "OEE_DATA"
  -> form.Show()
  -> SearchData()
```

历史路径：

```text
BtnHistory_Click
  -> GetCondition()
  -> QryServiceWithProcess.GetDataByCustQueryID("GetOEEUpdateHist_CUST", "0001", param)
```

# Data Dependencies

* [OEE_DATA](../tables/oee-data.md)
* [GetOEEData_CUST[0001]](../queries/get-oee-data-cust-0001.md)
* [GetOEEUpdateHist_CUST[0001]](../queries/get-oee-update-hist-cust-0001.md)
* [OEE](../metrics/oee.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

