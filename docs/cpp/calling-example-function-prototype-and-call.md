---
title: 呼叫範例：函式原型和呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508172"
---
# <a name="calling-example-function-prototype-and-call"></a>呼叫範例：函式原型和呼叫

## <a name="microsoft-specific"></a>Microsoft 特定的

下列範例示範使用各種呼叫慣例執行函式呼叫的結果。

這個範例是以下列函式架構為基礎。 以適當的呼叫慣例取代 `calltype`。

```
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

如需詳細資訊，請參閱 <<c0> [ 呼叫結果範例](../cpp/results-of-calling-example.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)