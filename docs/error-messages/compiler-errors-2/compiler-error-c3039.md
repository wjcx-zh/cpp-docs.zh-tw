---
title: 編譯器錯誤 C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: 69be1b25254119108e517cee2f1e14368e0163f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511612"
---
# <a name="compiler-error-c3039"></a>編譯器錯誤 C3039

'var': OpenMP 'for' 陳述式中的索引變數不可為削減變數

索引變數是隱含私用，因此變數不能用於封入 [parallel](../../parallel/openmp/reference/reduction.md) 指示詞的 [reduction](../../parallel/openmp/reference/parallel.md) 子句中。

## <a name="example"></a>範例

下列範例會產生 C3039：

```
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```