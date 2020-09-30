---
title: 編譯器錯誤 C3046
ms.date: 11/04/2016
f1_keywords:
- C3046
helpviewer_keywords:
- C3046
ms.assetid: 2e53d835-faa1-4ec0-9807-41f3dc552635
ms.openlocfilehash: cd7c934babe37def934b644ff4657ad63eb7676d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506228"
---
# <a name="compiler-error-c3046"></a>編譯器錯誤 C3046

OpenMP '#pragma omp sections' 區域中遺漏結構化區塊

[sections](../../parallel/openmp/reference/openmp-directives.md#sections-openmp) 指示詞具有空的程式碼區塊。

下列範例會產生 C3046：

```cpp
// C3046.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
/*
         ++n2;

         #pragma omp section
         {
            ++n3;
         }
*/
       }   // C3046 uncomment code to resolve this C3046
   }
}
```
