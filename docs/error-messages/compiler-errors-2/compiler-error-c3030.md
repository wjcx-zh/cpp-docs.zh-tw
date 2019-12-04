---
title: 編譯器錯誤 C3030
ms.date: 11/04/2016
f1_keywords:
- C3030
helpviewer_keywords:
- C3030
ms.assetid: de92fd7e-29ba-46e8-b43b-f4b985cd74de
ms.openlocfilehash: c9f22c01eb60ead22027cad2f59d9d2e95e01521
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757314"
---
# <a name="compiler-error-c3030"></a>編譯器錯誤 C3030

'var': 'reduction' 子句/指示詞中的變數不能有參考類型

您只可以將實值參數傳遞給特定子句 (例如 reduction 子句)。

下列範例會產生 C3030：

```cpp
// C3030.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

void test(int &r) {
   #pragma omp parallel reduction(+ : r)   // C3030
      ;
}

void test2(int r) {
   #pragma omp parallel reduction(+ : r)   // OK
      ;
}

int main(int argc, char** argv) {
   int& r = *((int*)argv);
   int s = *((int*)argv);

   #pragma omp parallel reduction(+ : r)   // C3030
      ;

   #pragma omp parallel reduction(+ : s)   // OK
      ;
}
```
