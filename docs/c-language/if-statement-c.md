---
title: if 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- else
- if
helpviewer_keywords:
- if keyword [C]
- else clauses
- else keyword [C]
- if keyword [C], if statement syntax
- nested statements
ms.assetid: d7fc16a0-fdbc-4f39-b596-76e1ca4ad4a5
ms.openlocfilehash: 6fe92d3f2927cd6c5b3df16850e2925fc42055d0
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684140"
---
# <a name="if-statement-c"></a>if 陳述式 (C)

**`if`** 語句控制條件式分支。 **`if`** 如果運算式的值為非零值，則會執行語句的主體。 語句的語法 **`if`** 有兩種形式。

## <a name="syntax"></a>語法

*selection 語句*： **if (**  *運算式*  **) **  *語句*

**if (***運算式***) ***語句* **`else`** *語句*          

在這兩種形式的 **`if`** 語句中，都會評估運算式（可以有任何值，但結構除外），包括所有副作用。

在第一種形式的語法中，如果 *expression* 為 true (非零值)，就會執行 *statement*。 如果 *expression* 是 false，則會忽略 *statement*。 在第二種形式的語法（使用 **`else`** ）中，如果*expression*為 false，則會執行第二個*語句*。 在這兩種形式中，控制項會從 **`if`** 語句傳遞至程式中的下一個語句，除非其中一個語句包含 **`break`** 、 **`continue`** 或 **`goto`** 。

以下是語句的範例 **`if`** ：

```C
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

在此範例中，如果 `y = x/i;` 大於 0，就會執行 `i` 陳述式。 如果 `i` 小於或等於 0，則會將 `i` 指派給 `x`，而將 `f( x )` 指派給 `y`。 請注意，形成子句的語句會以 **`if`** 分號結束。

當嵌套 **`if`** 語句和 **`else`** 子句時，請使用大括弧將語句和子句群組成複合陳述式，以明確地表達您的意圖。 如果沒有大括弧，編譯器會藉由將每個 **`else`** 與缺少的最接近的關聯，來解決多義性 **`if`** **`else`** 。

```C
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

**`else`** 子句與 **`if`** 此範例中的內部語句相關聯。 如果 `i` 小於或等於 0，則不會指派任何值給 `x`。

```C
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

此範例中內部語句周圍的大括弧會 **`if`** 使 **`else`** 子句成為外部語句的一部分 **`if`** 。 如果 `i` 小於或等於 0，會將 `i` 指派給 `x`。

## <a name="see-also"></a>另請參閱

[if-else 陳述式 (C++)](../cpp/if-else-statement-cpp.md)
