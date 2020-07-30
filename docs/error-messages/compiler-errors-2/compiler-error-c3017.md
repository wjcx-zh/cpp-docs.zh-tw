---
title: 編譯器錯誤 C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: 34347abffd91246ada080d19fee88ee09c8fce99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232062"
---
# <a name="compiler-error-c3017"></a>編譯器錯誤 C3017

OpenMP 'for' 陳述式中的終止測試格式不當

**`for`** OpenMP 語句中的迴圈必須完整且明確指定。

下列範例會產生 C3017：

```cpp
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```
