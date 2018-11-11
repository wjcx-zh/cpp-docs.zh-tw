---
title: continue 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: db3ed1d1575a52b8d54466f763f348821c458f31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587158"
---
# <a name="continue-statement-c"></a>continue 陳述式 (C)

`continue` 陳述式會將控制項傳遞至本身所在最靠近的封閉 `do`、`for` 或 `while` 陳述式的下一個反覆項目，並略過 `do`、`for` 或 `while` 陳述式主體中的其餘陳述式。

## <a name="syntax"></a>語法

*jump-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**繼續 ;**

`do`、`for` 或 `while` 陳述式的下一個反覆項目判斷方式如下：

- 在 `do` 或 `while` 陳述式內，下一個反覆項目是藉由重新評估 `do` 或 `while` 陳述式的運算式開始。

- `continue` 陳述式中的 `for` 陳述式會造成評估 `for` 陳述式的迴圈運算式。 然後，編譯器會重新評估條件運算式，並且根據結果結束或反覆運算陳述式主體。 如需 `for` 陳述式和其非終端項的詳細資訊，請參閱 [for 陳述式](../c-language/for-statement-c.md)。

這是 `continue` 陳述式的範例：

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

在此範例中，如果 `i` 大於 0，就會執行陳述式主體。 第一個 `f(i)` 會指派給 `x`，而如果 `x` 等於 1，就會執行 `continue` 陳述式。 主體中的其餘陳述式都會加以忽略，並且於迴圈的頂端透過評估迴圈的測試繼續執行。

## <a name="see-also"></a>請參閱

[continue 陳述式](../cpp/continue-statement-cpp.md)