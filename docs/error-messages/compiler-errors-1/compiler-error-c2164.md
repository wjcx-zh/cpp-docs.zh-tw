---
title: 編譯器錯誤 C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 3b1c7a94dfca1c2767e14f96204ecda670c8a586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460810"
---
# <a name="compiler-error-c2164"></a>編譯器錯誤 C2164

'function': 未宣告的內建函式

`intrinsic` Pragma 會使用未宣告的函式 (只會發生 **/Oi**)。 或者，但不包括其標頭檔所使用的其中一個編譯器內建函式。

下列範例會產生 C2164:

```
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```