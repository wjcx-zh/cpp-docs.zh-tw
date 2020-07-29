---
title: 編譯器錯誤 C3019
ms.date: 11/04/2016
f1_keywords:
- C3019
helpviewer_keywords:
- C3019
ms.assetid: 31a6d9b6-d29f-4499-9ad8-48dd751e87c7
ms.openlocfilehash: 5275ee6dd6680da3bf3aae0b657997f264762163
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232036"
---
# <a name="compiler-error-c3019"></a>編譯器錯誤 C3019

OpenMP ' for ' 語句中的增量格式不正確

OpenMP 迴圈的遞增部分 **`for`** 必須在運算子的左邊和右邊使用索引變數。

下列範例會產生 C3019：

```cpp
// C3019.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 1, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i = j + n)   // C3019
      // Try the following line instead:
      // for (i = 0; i < 10; i++)
         j *= 2;
   }
}
```
