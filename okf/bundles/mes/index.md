# MES CP OEE 与板卡知识包

本 bundle 是按 OKF 第一阶段生成的 MES 本地数据知识包，聚焦一个可验证的数据域：CP 工艺设备配置、OEE 报表、FUNC00757 板卡差额。

## Datasets

* [MES CP OEE Card Domain](datasets/mes-cp-oee-card-domain.md) - 连接 MDM 工艺配置、MES 运行态设备状态、OEE 数据与板卡报表的知识域。

## Tables

* [PROC_EQP](tables/proc-eqp.md) - 工艺规则下的设备配置，连接产品工艺、工站、设备、Recipe、针卡组、Device、DUT。
* [ET_PROC_CARD](tables/et-proc-card.md) - 工艺设备所需板卡配置，是 `REQUIRED_PC_CARD` 的来源。
* [EQP](tables/eqp.md) - 设备主档，FUNC00757 中同时承载 Prober 与 Tester 设备信息。
* [EQP_STATE](tables/eqp-state.md) - 设备运行态，提供当前设备上的 `PROD_ID`。
* [ET_PROBER_TESTER](tables/et-prober-tester.md) - Prober 与 Tester 的绑定关系。
* [CUST_CARD_INFO](tables/cust-card-info.md) - Tester 实际板卡登记来源。
* [OEE_DATA](tables/oee-data.md) - OEE 报表编辑和统计的数据对象。

## Reports

* [FUNC00757 Prober Tester 板卡匹配报表](reports/func00757.md) - 查询 Prober、Tester、产品、实际板卡、所需板卡与 `CARD_GAP`。
* [FrmOEEReport OEE 报表](reports/oee-report.md) - 查询、编辑和汇总 OEE 数据。

## Metrics

* [CARD_GAP](metrics/card-gap.md) - Tester 实际板卡比产品所需板卡多出的部分。
* [OEE](metrics/oee.md) - `QTY / ESTIMATE_QTY` 的报表汇总指标。

## Queries

* [FUNC00757_SELECT[0001]](queries/func00757-select-0001.md) - FUNC00757 的客户化查询契约。
* [GetOEEData_CUST[0001]](queries/get-oee-data-cust-0001.md) - OEE 数据读取查询。
* [GetOEEUpdateHist_CUST[0001]](queries/get-oee-update-hist-cust-0001.md) - OEE 更新历史查询。

## References

* [源码与文档证据](references/source-evidence.md) - 本 bundle 的来源文件、CodeGraph 查询、私域知识命中范围与边界。
