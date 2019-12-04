---
title: 編譯器錯誤 C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: b066e813203f10b902e49a62af97a9a041874752
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742115"
---
# <a name="compiler-error-c3020"></a>編譯器錯誤 C3020

' var '： OpenMP ' for ' 迴圈的索引變數無法在迴圈主體中修改

OpenMP `for` 迴圈可能無法修改 `for` 迴圈主體中的索引（迴圈計數器）。

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

使用[lastprivate](../../parallel/openmp/reference/lastprivate.md)宣告的變數不能當做平行處理迴圈內的索引使用。

下列範例會為第二個 lastprivate 提供 C3020，因為該 lastprivate 會在最外層的 for 迴圈中觸發對 idx_a 的寫入。 第一個 lastprivate 不會產生錯誤，因為該 lastprivate 會觸發最外層 for 迴圈外 idx_a 的寫入（技術上，最後一個反復專案的結尾）。 下列範例會產生 C3020。

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
