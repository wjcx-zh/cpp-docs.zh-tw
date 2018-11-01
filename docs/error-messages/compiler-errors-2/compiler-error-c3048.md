---
title: 編譯器錯誤 C3048
ms.date: 11/04/2016
f1_keywords:
- C3048
helpviewer_keywords:
- C3048
ms.assetid: 48e07091-94d9-471d-befe-7e2507631edd
ms.openlocfilehash: 451ae87f26357f47df4efdaa4393450f660a9000
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502426"
---
# <a name="compiler-error-c3048"></a>編譯器錯誤 C3048

'#pragma omp atomic' 後面的運算式格式指定錯誤

不正確地指定不可部分完成的指示詞。

下列範例會產生 C3048：

```
// C3048.cpp
// compile with: /openmp vcomps.lib
#include "omp.h"
#include <stdio.h>

int main() {
   int a[10];
   omp_set_num_threads(4);
   #pragma omp parallel
   {
      #pragma omp atomic
      a[0] = 1;   // C3048
      // try the following line instead
      // a[0] += 1;
   }
}
```