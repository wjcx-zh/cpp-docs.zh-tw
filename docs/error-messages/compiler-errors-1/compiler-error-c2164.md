---
title: 編譯器錯誤 C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 74c4f0e24f21f21d7a7015a20cb0e27ac635c467
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301908"
---
# <a name="compiler-error-c2164"></a>編譯器錯誤 C2164

' function '：內建函式未宣告

`intrinsic` pragma 使用未宣告的函式（僅發生在 **/Oi**）。 或者，使用其中一個編譯器內建函式，而不包含其標頭檔。

下列範例會產生 C2164：

```c
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```
