---
title: 編譯器錯誤 C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: 9b1efc0969373b6a91b0800ae71477b2371814bb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501436"
---
# <a name="compiler-error-c3059"></a>編譯器錯誤 C3059

'var': 'threadprivate' 符號不可使用在 'clause' 子句

子句中使用了 [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 符號。

下列範例會產生 C3059：

```cpp
// C3059.cpp
// compile with: /openmp
#include "omp.h"
int x, y;
#pragma omp threadprivate(x, y)

int main() {
   #pragma omp parallel private(x, y)   // C3059
   {
      x = y;
   }
}
```

可能的解決方式：

```cpp
// C3059b.cpp
// compile with: /openmp
#include "omp.h"
int x = 0, y = 0;

int main() {
   #pragma omp parallel firstprivate(y) private(x)
   {
      x = y;
   }
}
```
