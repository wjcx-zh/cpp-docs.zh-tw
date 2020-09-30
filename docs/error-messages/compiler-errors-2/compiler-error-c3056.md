---
title: 編譯器錯誤 C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: dd000e56d5fc24929e4d06e1bf0100ad9647610a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501597"
---
# <a name="compiler-error-c3056"></a>編譯器錯誤 C3056

'symbol': 符號和 'threadprivate' 指示詞不在同一個範圍內

[threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) 子句中所使用的符號必須與 `threadprivate` 子句位於相同的範圍中。

下列範例會產生 C3056：

```cpp
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

可能的解決方式：

```cpp
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
