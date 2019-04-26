---
title: 編譯器錯誤 C3044
ms.date: 11/04/2016
f1_keywords:
- C3044
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
ms.openlocfilehash: 0fb63d63ce9bdf0979382887164056dcdb288bd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187573"
---
# <a name="compiler-error-c3044"></a>編譯器錯誤 C3044

'section' : 只允許以巢狀方式直接放在 OpenMP 'sections' 指示詞之下

編譯器發現 `section` 指示詞的使用方式錯誤。 如需詳細資訊，請參閱 [章節](../../parallel/openmp/reference/sections-openmp.md)。

下列範例會產生 C3044：

```
// C3044.cpp
// compile with: /openmp /c
#include "omp.h"
int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         ++n2;
      }

      #pragma omp section   // C3044
      {
         ++n3;
      }
   }

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {
         #pragma omp section   // OK
         {
            ++n3;
         }
      }
   }
}
```