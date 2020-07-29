---
title: continue 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 3cf5d1c25b8edc70bd686ca26ad98b15b970383c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218906"
---
# <a name="continue-statement-c"></a>continue 陳述式 (C)

**`continue`** 語句會將控制項傳遞給 **`do`** 其出現之最接近之封入、或語句的下一個反復專案 **`for`** ，並 **`while`** 略過 **`do`** 、 **`for`** 或 **`while`** 語句主體中的任何剩餘語句。

## <a name="syntax"></a>語法

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**持續**

、或語句的下一個反復專案 **`do`** **`for`** **`while`** 會以下列方式決定：

- 在 **`do`** 或語句中 **`while`** ，下一個反復專案會先對或語句的運算式來開始 **`do`** **`while`** 。

- 語句 **`continue`** 中的語句 **`for`** 會導致評估語句的迴圈運算式 **`for`** 。 然後，編譯器會重新評估條件運算式，並且根據結果結束或反覆運算陳述式主體。 如需語句和其非終端項的詳細資訊，請參閱[For 語句](../c-language/for-statement-c.md) **`for`** 。

這是語句的範例 **`continue`** ：

```
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

在此範例中，如果 `i` 大於 0，就會執行陳述式主體。 第一個 `f(i)` 會指派給， `x` 然後，如果 `x` 等於1，則 **`continue`** 會執行語句。 主體中的其餘陳述式都會加以忽略，並且於迴圈的頂端透過評估迴圈的測試繼續執行。

## <a name="see-also"></a>另請參閱

[continue 語句](../cpp/continue-statement-cpp.md)
