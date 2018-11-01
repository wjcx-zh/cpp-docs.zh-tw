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
ms.openlocfilehash: c1d5fc926b396f1ec44b9e44e79721e2ca4a0908
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580904"
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元正和負運算子：+ 和 -

## <a name="syntax"></a>語法

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ 運算子

一元加法運算子的結果 (**+**) 是其運算元的值。 一元加法運算子的運算元必須屬於算術類型。

整數提升會在整數運算元上執行。 結果類型會是運算元提升後的類型。 因此，運算式`+ch`，其中`ch`別的**char**，型別會導致**int**; 的值是未修改。 請參閱[標準轉換](standard-conversions.md)如需如何執行提升的詳細資訊。

## <a name="--operator"></a>- 運算子

一元負運算子 (**-**) 會產生其運算元的負數。 一元負運算子的運算元必須是算術類型。

整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。 請參閱[標準轉換](standard-conversions.md)如需如何執行提升的詳細資訊。

## <a name="microsoft-specific"></a>Microsoft 專有的

不帶正負號數量的一元否定執行方式是 2^n 減去運算元的值，其中 n 是指定不帶正負號類型之物件的位元數。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)