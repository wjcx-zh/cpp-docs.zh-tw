---
title: '一元正和負運算子: + 和-|Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1441337275ac07b0d1ba39e8bfa34e7165f87f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="unary-plus-and-negation-operators--and--"></a>一元正和負運算子：+ 和 -
## <a name="syntax"></a>語法  
  
```  
  
+ cast-expression  
```  
  
```  
  
- cast-expression  
```  
  
## <a name="-operator"></a>+ 運算子  
 一元加法運算子的結果 (**+**) 是其運算元的值。 一元加法運算子的運算元必須屬於算術類型。  
  
 整數提升會在整數運算元上執行。 結果類型會是運算元提升後的類型。 因此，運算式 `+ch` (其中 `ch` 的類型為 `char`) 會得到 `int` 類型，且值未經修改。 請參閱[標準轉換](standard-conversions.md)如需有關如何進行升級。  
  
## <a name="--operator"></a>- 運算子  
 一元負運算子 (**-**) 會產生其運算元的負數。 一元負運算子的運算元必須是算術類型。  
  
 整數運算元上會執行整數提升，且結果類型是運算元提升後的類型。 請參閱[標準轉換](standard-conversions.md)如需如何執行提升的詳細資訊。  
  
## <a name="microsoft-specific"></a>Microsoft 專有的  
 不帶正負號數量的一元否定執行方式是 2^n 減去運算元的值，其中 n 是指定不帶正負號類型之物件的位元數。
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
