---
title: 編譯器錯誤 C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: ea6efbfa95992b04ade5496e8c7253ee87319a93
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508371"
---
# <a name="compiler-error-c3039"></a>編譯器錯誤 C3039

'var': OpenMP 'for' 陳述式中的索引變數不可為削減變數

索引變數是隱含私用，因此變數不能用於封入 [parallel](../../parallel/openmp/reference/openmp-clauses.md#reduction) 指示詞的 [reduction](../../parallel/openmp/reference/openmp-directives.md#parallel) 子句中。

## <a name="example"></a>範例

下列範例會產生 C3039：

```cpp
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
