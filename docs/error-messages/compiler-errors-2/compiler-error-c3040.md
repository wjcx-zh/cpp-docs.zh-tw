---
title: 編譯器錯誤 C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: 943c4b3da1a90c8636246032a3d8faf41ad4552a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508357"
---
# <a name="compiler-error-c3040"></a>編譯器錯誤 C3040

'var': 'reduction' 子句中的變數類型與削減運算子 'operator' 不相容

[reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 子句中的變數不能和削減運算子一起使用。

下列範例會產生 C3040：

```cpp
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```
