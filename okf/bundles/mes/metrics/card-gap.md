---
type: Metric
title: CARD_GAP
description: Tester 实际板卡配置比产品所需板卡配置多出的部分，只表达多余，不表达短缺。
resource: D:/Workspace/MES/MES_AI/backend/MES_SERVICE/nebula-mes-ext/src/main/java/com/nebula/mes/extension/object/generalReport/func00757/service/Func00757ServiceExt.java
tags: [mes, metric, func00757, card-gap]
timestamp: 2026-06-23T00:00:00+08:00
---

# Definition

`CARD_GAP` 表示 Tester 实际板卡配置比产品工艺所需板卡配置多出来的部分。

```text
CARD_GAP = adjustedActualCards - effectiveRequiredCards, only when result > 0
```

它不表达短缺板卡。如果实际少于所需，`CARD_GAP` 返回空字符串。

# Inputs

| Input | Meaning |
|---|---|
| `TESTER_CARD_DETAIL` | 实际板卡配置，来自 [CUST_CARD_INFO](../tables/cust-card-info.md) 的展示聚合。 |
| `REQUIRED_PC_CARD` | 产品工艺所需板卡，来自 [ET_PROC_CARD](../tables/et-proc-card.md)。 |

# Parsing Rules

* 常规格式：`数量*板卡类型,数量*板卡类型`。
* `TESTER_CARD_DETAIL` 可包含包装格式：`8*FPVI(8*FPVI10_PLUS)`、`3*DIO(1*DIO_PLUS,2*DIO_3.0)`。
* 括号外的 `FPVI(...)`、`DIO(...)` 是展示包装；括号内的特殊板卡才按原始板卡类型参与计算。
* 同一实际板卡类型重复出现时按 `SUM` 汇总。
* 同一需求板卡类型重复出现时按 `MAX` 去重语义处理。

# Special Card Rules

| Special Card | Can satisfy |
|---|---|
| `FPVI10_PLUS` | `FPVI` |
| `DIO_PLUS` | `DIO` |
| `DIO_3.0` | `DIO` 或 `DIO_PLUS` |

输出时必须保留实际多出来的原始板卡名，例如 `FPVI10_PLUS`、`DIO_PLUS`、`DIO_3.0`，不能统一折算成基础板卡名。

# Output

格式：

```text
数量*原始板卡类型,数量*原始板卡类型
```

无多余板卡时返回空字符串。

# Example

```text
Actual:   2*CBIT,12*FOVI,8*FPVI(8*FPVI10_PLUS),2*QTMU
Required: 2*CBIT,2*DIO,8*FOVI,8*FPVI10_PLUS,2*QTMU
CARD_GAP: 4*FOVI
```

# Relationships

* Report: [FUNC00757 Prober Tester 板卡匹配报表](../reports/func00757.md)
* Query: [FUNC00757_SELECT[0001]](../queries/func00757-select-0001.md)

# Citations

[1] [源码与文档证据](../references/source-evidence.md)

