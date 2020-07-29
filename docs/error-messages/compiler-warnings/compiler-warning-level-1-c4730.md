---
title: 編譯器警告 (層級 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: a132dcc795d6055c854a5ad147940868fe4e088b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228774"
---
# <a name="compiler-warning-level-1-c4730"></a>編譯器警告 (層級 1) C4730

' main '：混合 _m64 和浮點運算式可能會導致不正確的程式碼

函式會使用[__m64](../../cpp/m64.md)和 **`float`** / **`double`** 類型。 由於 MMX 和浮點暫存器共用相同的實體暫存器空間（無法同時使用），因此 **`__m64`** **`float`** / **`double`** 在相同的函式中使用和類型可能會導致資料損毀，可能會造成例外狀況。

若要安全地 **`__m64`** 在相同的函式中使用類型和浮點類型，每個使用其中一個類型的指令都應該以 **_m_empty （）** （適用于 MMX）或 **_m_femms （）** （適用于3DNow！）內建函式來分隔。

下列範例會產生 C4730：

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```
