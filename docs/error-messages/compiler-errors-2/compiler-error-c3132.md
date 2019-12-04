---
title: 編譯器錯誤 C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: d3ef68e693b77b72c1e4cc2590a404b09b38ab04
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760201"
---
# <a name="compiler-error-c3132"></a>編譯器錯誤 C3132

' function-parameter '：參數陣列只能套用至類型「單一維度 managed 陣列」的正式引數

<xref:System.ParamArrayAttribute> 屬性已套用至不是單一維度陣列的參數。

下列範例會產生 C3132：

```cpp
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK
```
