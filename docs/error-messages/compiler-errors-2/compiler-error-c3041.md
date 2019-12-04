---
title: 編譯器錯誤 C3041
ms.date: 11/04/2016
f1_keywords:
- C3041
helpviewer_keywords:
- C3041
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
ms.openlocfilehash: f9f9b9a598760b251d911f3f0a5ddd1114dd764c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754936"
---
# <a name="compiler-error-c3041"></a>編譯器錯誤 C3041

'var'：'copyprivate' 子句中的變數在封入內容中必須是私用

在封入內容中不能共用傳遞給 [copyprivate](../../parallel/openmp/reference/copyprivate.md) 的變數。

下列範例會產生 C3041：

```cpp
// C3041.cpp
// compile with: /openmp /c
#include "omp.h"
double d;
int main() {
   #pragma omp parallel shared(d)
   // try the following line instead
   // #pragma omp parallel private(d)
   {
      // or don't make d copyprivate
      #pragma omp single copyprivate(d)   // C3041
      {
      }
   }
}
```
