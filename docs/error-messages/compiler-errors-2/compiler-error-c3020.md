---
title: 編譯器錯誤 C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: cb32ceaf71d0a1c121b6e01e4b49f1db79a84d79
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506496"
---
# <a name="compiler-error-c3020"></a>編譯器錯誤 C3020

' var '： OpenMP ' for ' 迴圈的索引變數無法在迴圈主體中修改

OpenMP **`for`** 迴圈可能不會修改迴圈主體中的 index (迴圈計數器) **`for`** 。

下列範例會產生 C3020：

```cpp
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

使用 [lastprivate](../../parallel/openmp/reference/openmp-clauses.md#lastprivate) 宣告的變數不能當做平行迴圈內的索引使用。

下列範例會提供第二個 lastprivate 的 C3020，因為該 lastprivate 將會觸發對最外層 for 迴圈內 idx_a 的寫入。 第一個 lastprivate 並不會產生錯誤，因為 lastprivate 會在最後一個反復專案) 的最一端，于最外層的 (觸發寫入至外部 idx_a。 下列範例會產生 C3020。

```cpp
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

下列範例示範可能的解決方式：

```cpp
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```
