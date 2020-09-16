---
title: continue 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- continue
helpviewer_keywords:
- loop structures, continue keyword
- continue keyword [C]
ms.assetid: 969f293a-45fe-48a7-b4c6-287ba27a631d
ms.openlocfilehash: 27d1d0aa0e49c5c46e4ea4e010635ca0057c3f85
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684829"
---
# <a name="continue-statement-c"></a>continue 陳述式 (C)

**`continue`** 語句會將控制權傳遞給其出現之最接近封入、或語句的下一個反復專案 **`do`** ，並 **`for`** **`while`** 略過 **`do`** 、 **`for`** 或語句主體中的任何其餘語句 **`while`** 。

## <a name="syntax"></a>語法

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**接續**

、或語句的下一個反復專案 **`do`** **`for`** **`while`** 會依照下列方式決定：

- 在 **`do`** 或語句中 **`while`** ，下一次反覆運算的開頭是對 **`do`** 或語句的運算式 **`while`** 。

- **`continue`** 語句中的語句 **`for`** 會讓語句的迴圈運算式 **`for`** 得以進行評估。 然後，編譯器會重新評估條件運算式，並且根據結果結束或反覆運算陳述式主體。 如需有關語句及其非終端項的詳細資訊，請參閱 [For 語句](../c-language/for-statement-c.md) **`for`** 。

這是語句的範例 **`continue`** ：

```C
while ( i-- > 0 )
{
    x = f( i );
    if ( x == 1 )
        continue;
    y += x * x;
}
```

在此範例中，如果 `i` 大於 0，就會執行陳述式主體。 第一個 `f(i)` 是指派給 `x` ; 然後，如果 `x` 等於1， **`continue`** 就會執行語句。 主體中的其餘陳述式都會加以忽略，並且於迴圈的頂端透過評估迴圈的測試繼續執行。

## <a name="see-also"></a>另請參閱

[continue 語句](../cpp/continue-statement-cpp.md)
