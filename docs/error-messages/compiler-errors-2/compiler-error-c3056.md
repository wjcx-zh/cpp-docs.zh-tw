---
title: 編譯器錯誤 C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: 97a403420e5923f23f804eeaff33af1698ff6a53
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761152"
---
# <a name="compiler-error-c3056"></a>編譯器錯誤 C3056

'symbol': 符號和 'threadprivate' 指示詞不在同一個範圍內

[threadprivate](../../parallel/openmp/reference/threadprivate.md) 子句中所使用的符號必須與 `threadprivate` 子句位於相同的範圍中。

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

可能的解決方案：

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
