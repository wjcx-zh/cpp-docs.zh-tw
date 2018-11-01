---
title: 編譯器錯誤 C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: 2b8edc506b6038ddec0ca265cafabbebf0428d1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612975"
---
# <a name="compiler-error-c3132"></a>編譯器錯誤 C3132

' 函式參數 ': 參數陣列只可以套用至類型 '維 managed 陣列' 的型式引數

[ParamArray](https://msdn.microsoft.com/library/system.paramarrayattribute.aspx)屬性已套用至不是一維陣列的參數。

下列範例會產生 C3132:

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK

```