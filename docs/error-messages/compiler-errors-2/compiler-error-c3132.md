---
title: 編譯器錯誤 C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: a4c6ce8005aecd094c57b3dbda5c95565deecb95
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519798"
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