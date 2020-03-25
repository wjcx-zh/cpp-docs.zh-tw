---
title: 呼叫範例：函式原型和呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: c41d7679be8b7faa3c8df1368d14815a1b840284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190166"
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

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
