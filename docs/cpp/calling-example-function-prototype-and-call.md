---
title: 呼叫範例：函式原型和呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: cbe9ee16db502c9e27dcbd74da4ef6a85f00960f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857628"
---
# <a name="calling-example-function-prototype-and-call"></a>呼叫範例：函式原型和呼叫

**Microsoft 專屬**

下列範例示範使用各種呼叫慣例執行函式呼叫的結果。

這個範例是以下列函式架構為基礎。 以適當的呼叫慣例取代 `calltype`。

```cpp
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

如需詳細資訊，請參閱[呼叫範例的結果](../cpp/results-of-calling-example.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[呼叫慣例](../cpp/calling-conventions.md)