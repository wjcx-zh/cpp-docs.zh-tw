---
title: 一元正和負運算子：+ 和 -
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: 83fedd9d3cc6cd7c08ba79d2ed83e9f62d919e29
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857238"
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元正和負運算子：+ 和 -

## <a name="syntax"></a>語法

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ 運算子

一元加號運算子（ **+** ）的結果是其運算元的值。 一元加法運算子的運算元必須屬於算術類型。

整數提升會在整數運算元上執行。 結果類型會是運算元提升後的類型。 因此，運算式 `+ch`，其中 `ch` 的類型為**char**，會產生類型**int**。此值未修改。 如需如何完成升級的詳細資訊，請參閱[標準轉換](standard-conversions.md)。

## <a name="--operator"></a>- 運算子

一元負運算子（ **-** ）會產生其運算元的負數。 一元負運算子的運算元必須是算術類型。

整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。 如需如何執行升級的詳細資訊，請參閱[標準轉換](standard-conversions.md)。

**Microsoft 專屬**

不帶正負號數量的一元否定執行方式是 2^n 減去運算元的值，其中 n 是指定不帶正負號類型之物件的位元數。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)