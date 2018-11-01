---
title: 編譯器錯誤 C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: 0e2d8e70dcc9b23c56a321487cd4b933a1086387
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491269"
---
# <a name="compiler-error-c3020"></a>編譯器錯誤 C3020

'var': OpenMP 'for' 迴圈的索引變數不能修改在迴圈主體中

OpenMP`for`迴圈可能不會修改的本文中的索引 （迴圈計數器）`for`迴圈。

下列範例會產生 C3020:

```
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

以宣告的變數[lastprivate](../../parallel/openmp/reference/lastprivate.md)不能用做平行化迴圈內的索引。

下列範例會針對第二個 lastprivate 提供 C3020，因為該 lastprivate 會觸發寫入 idx_a 中最外層的迴圈。 第一個 lastprivate 不會發生錯誤，因為該 lastprivate 觸發 idx_a 之外最外層寫入 for 迴圈 （技術上來說，在結尾的最後一個反覆項目）。 下列範例會產生 C3020。

```
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

```
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