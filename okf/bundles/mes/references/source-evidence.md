---
type: Reference
title: 源码与文档证据
description: MES OKF bundle 的来源文件、CodeGraph 查询、私域知识命中范围和已知边界。
resource: D:/Workspace/MES/MES_AI
tags: [mes, evidence, okf]
timestamp: 2026-06-23T00:00:00+08:00
---

# Generation Context

本 bundle 按 `03-Resources/待实践/knowledge-catalog-说明和使用文档.md` 的“第一阶段：只用 OKF 思路，不碰 GCP 写入”生成。

输出目录：

```text
D:/Workspace/knowledge-catalog/okf/bundles/mes
```

# Private Knowledge Precheck

命中的私域知识索引域：

* 数据模型与表关系。
* 查询与 SQL 规范。
* 前端页面与交互规范。

延迟加载文档：

* `docs/私域知识/MES_SERVICE/02_数据模型.md`
* `docs/私域知识/MES_UI/05_开发规范.md`
* `docs/私域知识工程体系产出/知识沉淀/数据模型手册.md`
* `docs/私域知识工程体系产出/知识沉淀/查询规格卡片模板-MSSQL.md`

# CodeGraph

MES 仓库存在 `.codegraph/`。初次在沙箱中运行 `codegraph explore` 和 `codegraph status` 时出现 `unable to open database file`；提权读取后 `codegraph status` 显示索引正常：

```text
Files: 3,565
Nodes: 109,972
Edges: 306,709
DB Size: 381.68 MB
Index is up to date
```

使用过的 CodeGraph 查询：

```text
codegraph explore "MES data catalog for PROC_EQP OEE_DATA FUNC00757 TESTER_CARD_DETAIL REQUIRED_PC_CARD FrmOEEReport Func00757ServiceExt"
codegraph explore "PROC_EQP PFOAddData OKData ProcEqpManagement MdmServices.ProcEqpSave PROC_EQP_HIST OEE_TIME release OeeTimeInfo"
```

# Source Anchors

| Area | Source |
|---|---|
| FUNC00757 Java service | `backend/MES_SERVICE/nebula-mes-ext/src/main/java/com/nebula/mes/extension/object/generalReport/func00757/service/Func00757ServiceExt.java` |
| FUNC00757 constants | `backend/MES_SERVICE/nebula-mes-ext/src/main/java/com/nebula/mes/extension/object/generalReport/func00757/service/Func00757ReportConstants.java` |
| FUNC00757 method summary | `docs/specs/func00757-card-gap-java/05_method_summary.md` |
| FUNC00757 SQL explanation | `FUNC00757_SQL说明.md` |
| OEE report UI | `frontend/MES_UI/Nebula.MOS.Module.Inquiry/Lot/FrmOEEReport.cs` |
| OEE edit popup | `frontend/MES_UI/Nebula.MOS.Module/Popup/FrmEditOEEData.cs` |
| PRP release and PROC_EQP copy | `backend/MDM_SERVICE/nebula-mdm-server/src/main/java/com/nebula/mdm/management/process/PrpManagement.java` |
| Data model handbook | `docs/私域知识工程体系产出/知识沉淀/数据模型手册.md` |
| Query card template | `docs/私域知识工程体系产出/知识沉淀/查询规格卡片模板-MSSQL.md` |

# Boundaries

* 运行时 `CUST_QUERY` SQL 大多不在仓库源码内。本 bundle 对 `FUNC00757_SELECT[0001]` 使用仓库内 `FUNC00757_SQL说明.md` 和规格文档作为证据。
* `GetOEEData_CUST[0001]` 与 `GetOEEUpdateHist_CUST[0001]` 的 SQL 正文未在源码中确认，本 bundle 只记录可见调用点和字段依赖。
* 第一版只覆盖 CP OEE 与板卡差额领域，不覆盖全部 MES 数据资产。
* 本 bundle 未连接 Google Cloud Knowledge Catalog，也未执行 `kcmd push`。
