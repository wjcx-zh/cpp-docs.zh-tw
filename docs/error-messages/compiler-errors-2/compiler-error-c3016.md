---
title: 編譯器錯誤 C3016
ms.date: 11/04/2016
f1_keywords:
- C3016
helpviewer_keywords:
- C3016
ms.assetid: 3423467e-e8bb-4f35-b4db-7925cafa74c1
ms.openlocfilehash: 728d6042b192e0c309f8e9a6e473108f23dbbdf9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232075"
---
# <a name="compiler-error-c3016"></a>編譯器錯誤 C3016

'var': OpenMP 'for' 陳述式中的索引變數必須具有帶正負號的整數類資料類型

OpenMP 語句中的索引變數 **`for`** 必須是帶正負號的整數類資料類型。

下列範例會產生 C3016：

```cpp
// C3016.cpp
// compile with: /openmp
int main()
{
   #pragma omp parallel
   {
      unsigned int i = 0;
      // Try the following line instead:
      // int i = 0;

      #pragma omp for
      for (i = 0; i <= 10; ++i)   // C3016
      {
      }
   }
}
```
