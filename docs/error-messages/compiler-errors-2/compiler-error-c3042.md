---
title: 編譯器錯誤 C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 8cd27f492a72277c383afa5ca335a073b1a0519c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506399"
---
# <a name="compiler-error-c3042"></a>編譯器錯誤 C3042

'copyprivate' 和 'nowait' 子句不可以同時出現在 OpenMP 'directive' 指示詞中

在指定的指示詞上， [copyprivate](../../parallel/openmp/reference/openmp-clauses.md#copyprivate) 與 [nowait](../../parallel/openmp/reference/openmp-clauses.md#nowait) 子句互斥。 若要修正這個錯誤，請移除 `copyprivate` 及/或 `nowait` 子句。

下列範例會產生 C3042：

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
