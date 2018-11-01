---
title: 編譯器錯誤 C3054
ms.date: 11/04/2016
f1_keywords:
- C3054
helpviewer_keywords:
- C3054
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
ms.openlocfilehash: c45a59f136b989190a46fd9fbe00fdd0e4b89527
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470123"
---
# <a name="compiler-error-c3054"></a>編譯器錯誤 C3054

目前在泛型類別或函式中不支援 '#pragma omp parallel'

如需詳細資訊，請參閱 <<c0> [ 泛型](../../windows/generics-cpp-component-extensions.md)並[OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C3054。

```
// C3054.cpp
// compile with: /openmp /clr /c
#include <omp.h>

ref struct MyBaseClass {
   // Delete the following 7 lines to resolve.
   generic <class ItemType>
   void Test(ItemType i) {   // C3054
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }

   // OK
   void Test2() {
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }
};
```