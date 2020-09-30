---
title: 編譯器錯誤 C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 7da7dcf1f03c05511ba4bb970e898bc06b9ae3bd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508419"
---
# <a name="compiler-error-c3038"></a>編譯器錯誤 C3038

'var': 'private' 子句中的變數在封入內容中不可為削減變數

在平行指示詞的 [reduction](../../parallel/openmp/reference/openmp-clauses.md#reduction) 子句中出現的變數，不能指定於繫結至平行建構之工作共用指示詞的 [private](../../parallel/openmp/reference/openmp-clauses.md#private-openmp) 子句中。

下列範例會產生 C3038：

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
