---
title: 編譯器錯誤 C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 4347e5ee0e61ada700082b4954b616ce894e57b9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761386"
---
# <a name="compiler-error-c3042"></a>編譯器錯誤 C3042

'copyprivate' 和 'nowait' 子句不可以同時出現在 OpenMP 'directive' 指示詞中

在指定的指示詞上， [copyprivate](../../parallel/openmp/reference/copyprivate.md) 與 [nowait](../../parallel/openmp/reference/nowait.md) 子句互斥。 若要修正這個錯誤，請移除 `copyprivate` 及/或 `nowait` 子句。

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
