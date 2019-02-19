---
title: switch 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
ms.openlocfilehash: 0f781147bf4ed020cf925ca29c2ba1b0f601cde1
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148188"
---
# <a name="switch-statement-c"></a>switch 陳述式 (C)

`switch` 和 **case** 陳述式有助於控制複雜的條件作業和分支作業。 `switch` 陳述式會將控制權轉移到其主體中的陳述式。

## <a name="syntax"></a>語法

*selection-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**交換 (** *運算式* **)** *陳述式*

*labeled-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *constant-expression*  **:**  *陳述式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**預設 :**  *陳述式*

控制權會傳遞給 **case** *constant-expression* 與 **switch (** *expression* **)** 的值相符之陳述式。 `switch` 陳述式可包含任何數目的 **case** 執行個體；不過，相同 `switch` 陳述式內的兩個 case 常數不能有相同的值。 陳述式主體的執行會從選取的陳述式開始，並且繼續執行直到主體結尾或直到 **break** 陳述式將控制權轉移到主體以外。

`switch` 陳述式的用法通常如下所示：

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

您可以使用 **break** 陳述式結束處理 `switch` 陳述式內的特定大小寫，以及分支到 `switch` 陳述式的結尾。 若沒有 **break**，程式會繼續到下一個大小寫，並且執行陳述式直到出現 **break** 或達到陳述式結尾為止。 在某些情況下，您可能希望繼續執行。

如果所有 **case** *constant-expression* 皆不等於 **switch (** *expression* **)** 的值，則會執行 **default** 陳述式。 如果略過 **default** 陳述式，且找不到相符的 **case**，就不會執行 `switch` 主體中的任何陳述式。 最多可以有一個 **default** 陳述式。 **default** 陳述式不需要出現在結尾，可以出現在 `switch` 陳述式主體中的任何位置。 **case** 或 **default** 標籤只能出現在 `switch` 陳述式內。

`switch` *expression* 和 **case** *constant-expression* 必須是整數類型。 每個 **case** *constant-expression* 的值在陳述式主體中必須是唯一的。

`switch` 陳述式的 **case** 和 **default** 標籤只有在決定從陳述式主體中的哪一個位置開始執行的初始測試中具有意義。 switch 陳述式可以是巢狀結構。 所有靜態變數都會在執行之前初始化為任何 `switch` 陳述式。

> [!NOTE]
> 宣告可以出現在形成 `switch` 主體的複合陳述式的開頭，但不會執行包含在宣告中的初始化。 `switch` 陳述式會將控制權直接轉移給主體中的可執行陳述式，並且略過包含初始化的程式行。

下列範例說明 `switch` 陳述式：

```C
switch( c )
{
    case 'A':
        capa++;
    case 'a':
        lettera++;
    default :
        total++;
}
```

如果 `c` 等於 `'A'`，本範例中 `switch` 主體的三個陳述式會全數執行，因為 **break** 陳述式沒有在下一個大小寫之前出現。 執行控制權會轉移到第一個陳述式 (`capa++;`)，並且依序繼續執行該主體的其餘部分。 如果 `c` 等於 `'a'`，`lettera` 和 `total` 會遞增。 如果 `total` 不等於 `c` 或 `'A'`，則只有 `'a'` 會遞增。

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

在此範例中，**break** 陳述式會接在 `switch` 主體的每個陳述式之後。 **break** 陳述式會在執行某個陳述式之後強制從陳述式主體結束。 如果 `i` 等於 -1，則只有 `n` 會遞增。 `n++;` 陳述式後面的 **break** 會導致將執行控制權傳遞到陳述式主體之外，並且略過剩餘的陳述式。 同樣地，如果，`i` 等於 0，只有 `z` 會遞增；如果 `i` 等於 1，只有 `p` 會遞增。 最終的 **break** 陳述式並不是絕對必要的，因為控制權會在複合陳述式的結尾傳遞到主體以外，但為了一致性會保留此陳述式。

如下列範例所示，單一陳述式可以多載多個 **case** 標籤：

```C
case 'a' :
case 'b' :
case 'c' :
case 'd' :
case 'e' :
case 'f' :  hexcvt(c);
```

在此範例中，如果 *constant-expression* 等於 `'a'` 與 `'f'` 之間的任何字母，則會呼叫 `hexcvt` 函式。

**Microsoft 專屬**

Microsoft C 不會限制 `switch` 陳述式中 case 值的數目。 此數目會受到可用記憶體的限制。 ANSI C 要求在 `switch` 陳述式中允許至少 257 個 case 標籤。

Microsoft C 預設會啟用 Microsoft 擴充功能。 使用 /Za 編譯器選項可停用這些擴充功能。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[switch 陳述式 (C++)](../cpp/switch-statement-cpp.md)
