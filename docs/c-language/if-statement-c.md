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
ms.openlocfilehash: 67cdae033c3c8669c8bc7ae1d2e3584ef68498f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227838"
---
# <a name="if-statement-c"></a>if 陳述式 (C)

**`if`** 語句會控制條件分支。 **`if`** 如果運算式的值不是零，就會執行語句的主體。 語句的語法 **`if`** 有兩種形式。

## <a name="syntax"></a>語法

*selection 語句*： **if （**  *expression*  **）**  *語句*

**if （***運算式***）***語句* **`else`** *語句*          

在這兩種形式的 **`if`** 語句中，都會評估運算式（可以有任何值除外的結構），包括所有的副作用。

在第一種形式的語法中，如果 *expression* 為 true (非零值)，就會執行 *statement*。 如果 *expression* 是 false，則會忽略 *statement*。 在第二種形式的語法（使用 **`else`** ）中，如果*expression*為 false，則會執行第二個*語句*。 使用這兩種形式時， **`if`** 除非其中一個語句包含、或，否則控制權會從語句傳遞至程式中的下一個語句 **`break`** **`continue`** **`goto`** 。

以下是語句的範例 **`if`** ：

```
if ( i > 0 )
    y = x / i;
else
{
    x = i;
    y = f( x );
}
```

在此範例中，如果 `y = x/i;` 大於 0，就會執行 `i` 陳述式。 如果 `i` 小於或等於 0，則會將 `i` 指派給 `x`，而將 `f( x )` 指派給 `y`。 請注意，構成子句的語句會以 **`if`** 分號結尾。

當嵌套 **`if`** 語句和 **`else`** 子句時，請使用大括弧將語句和子句分組成複合陳述式，以表達您的意圖。 如果沒有大括弧，編譯器會將每個 **`else`** 與缺少的最接近的產生關聯，藉以解決多義性 **`if`** **`else`** 。

```
if ( i > 0 )           /* Without braces */
    if ( j > i )
        x = j;
    else
        x = i;
```

**`else`** 子句會與 **`if`** 此範例中的內部語句相關聯。 如果 `i` 小於或等於 0，則不會指派任何值給 `x`。

```
if ( i > 0 )
{                      /* With braces */
    if ( j > i )
        x = j;
}
else
    x = i;
```

在此範例中，內部語句周圍的大括弧會 **`if`** 使 **`else`** 子句成為外部 **`if`** 語句的一部分。 如果 `i` 小於或等於 0，會將 `i` 指派給 `x`。

## <a name="see-also"></a>另請參閱

[if-else 陳述式 (C++)](../cpp/if-else-statement-cpp.md)
