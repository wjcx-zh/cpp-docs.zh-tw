---
title: 編譯器錯誤 C3055
ms.date: 11/04/2016
f1_keywords:
- C3055
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
ms.openlocfilehash: ed0f031fcd0ff0c621556bf73572d720fc2c1352
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501620"
---
# <a name="compiler-error-c3055"></a>編譯器錯誤 C3055

'symbol' : 符號必須先使用在 'threadprivate' 指示詞中，然後才能夠被參考

符號已被參考並接著用於 [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 子句中，這不是允許的做法。

下列範例會產生 C3055：

```cpp
// C3055.cpp
// compile with: /openmp
int x, y;
int z = x;
#pragma omp threadprivate(x, y)   // C3055

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

可能的解決方式：

```cpp
// C3055b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
