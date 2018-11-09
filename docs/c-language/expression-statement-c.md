---
title: 運算陳述式 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- statements, expression
- expression statements
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
ms.openlocfilehash: b825e88703e1913d9b6d916360174060854c632a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667463"
---
# <a name="expression-statement-c"></a>運算陳述式 (C)

執行運算陳述式時，會根據[運算式和指派](../c-language/expressions-and-assignments.md)中所列的規則，以求出運算式的值。

## <a name="syntax"></a>語法

*expression-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*<sub>opt</sub> **;**

在執行下一個陳述式之前，會完成運算式求值的所有副作用。 一個空的運算陳述式稱為 Null 陳述式。 如需詳細資訊，請參閱 [Null 陳述式](../c-language/null-statement-c.md)。

這些範例示範了運算陳述式。

```C
x = ( y + 3 );            /* x is assigned the value of y + 3  */
x++;                      /* x is incremented                  */
x = y = 0;                /* Both x and y are initialized to 0 */
proc( arg1, arg2 );       /* Function call returning void      */
y = z = ( f( x ) + 3 );   /* A function-call expression        */
```

在最後一個陳述式中，函式呼叫運算式、運算式的值 (包括由函式傳回的所有值) 會增加 3，然後指派給變數 `y` 和 `z`。

## <a name="see-also"></a>請參閱

[陳述式](../c-language/statements-c.md)