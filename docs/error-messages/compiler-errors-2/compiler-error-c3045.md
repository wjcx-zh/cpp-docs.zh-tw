---
title: 編譯器錯誤 C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: fc5c2b526133ea0de70d11c3a01269436701de79
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506279"
---
# <a name="compiler-error-c3045"></a>編譯器錯誤 C3045

OpenMP 'sections' 指示詞後面必須是複合陳述式。 遺漏 '{'

以大括弧分隔的程式碼區塊必須接在 [sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) 指示詞後面。

下列範例會產生 C3045：

```cpp
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```
