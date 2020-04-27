---
title: switch語句（C）
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167672"
---
# <a name="opno-locswitch-statement-c"></a>switch語句（C）

**switch** 和**case** 語句有助於控制複雜的條件式和分支作業。 **switch** 語句會將控制權轉移到其主體中的語句。

## <a name="syntax"></a>語法

*選取範圍-語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***expression* **`)`** *語句*

加上*標籤的語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *常數運算式*  **`:`**  *語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *句*

控制權會傳遞給其**case** *常數運算式*符合** switch （** *expression* **）** 值的語句。 **switch** 語句可包含任何數目的**case** 實例。 不過，相同**switch** 語句case內的兩個常數不能有相同的值。 語句主體的執行會從選取的語句開始。 它會繼續進行，直到主體結束為止，或直到**break** 語句將控制權轉移到主體為止。

使用**switch** 語句通常看起來像這樣：

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

您可以使用**break** 語句來結束處理**switch** 語句內的特定標記語句。 它會分支到**switch** 語句的結尾。 若**break** 沒有，程式會繼續進行下一個標記的語句，執行語句直到**break** 到達或語句結尾為止。 在某些情況下，可能會需要此接續。

如果**default** 沒有**case** *常數運算式*等於** switch （** *expression* **）** 的值，就會執行語句。 如果沒有**default** 語句，而且找不到**case** 相符的內容，就不會執行**switch** 主體中的任何語句。 最多隻能有一個**default** 語句。 **default** 語句不一定要放在結尾。 它可能會出現在**switch** 語句主體中的任何位置。 **case** 或**default** 標籤只能出現在**switch** 語句內。

**switch** *運算式*和**case** *常數運算式*的類型必須是整數。 每個**case** *常數運算式*的值在語句主體中必須是唯一的。

語句主體的**case** 和**default** 標籤只有在決定在語句主體中開始執行之處的初始測試中才有意義。 **switch** **switch** 語句可以嵌套。 在執行任何**switch** 語句之前，會先初始化任何靜態變數。

> [!NOTE]
> 宣告可以出現在構成**switch** 主體的複合陳述式的開頭，但不會執行包含在宣告中的初始化。 **switch** 語句會將控制權直接傳送至主體內的可執行語句，略過包含初始化的程式列。

下列範例說明**switch** 語句：

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

**switch** 如果`c`等於`'A'`，則會執行此範例中主體的三個語句，因為在下列**break** case之前不會出現任何語句。 執行控制權會轉移到第一個陳述式 (`capital_a++;`)，並且依序繼續執行該主體的其餘部分。 如果 `c` 等於 `'a'`，`letter_a` 和 `total` 會遞增。 只有`total`當不等於`c` `'A'`或`'a'`時，才會遞增。

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

在此範例中， **break** 語句會遵循**switch** 主體的每個語句。 **break** 語句會在執行一個語句之後，強制從語句主體結束。 如果 `i` 等於 -1，則只有 `n` 會遞增。 **break** 下列語句`n++;`會導致執行控制傳遞語句主體，略過其餘語句。 同樣地，如果，`i` 等於 0，只有 `z` 會遞增；如果 `i` 等於 1，只有 `p` 會遞增。 最後**break** 的語句並不是絕對必要的，因為控制權會在複合陳述式的結尾處傳入主體。 其中包含一致性。

單一語句可以包含多個**case** 標籤，如下列範例所示：

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

在此範例中，如果 *constant-expression* 等於 `'a'` 與 `'f'` 之間的任何字母，則會呼叫 `convert_hex` 函式。

### <a name="microsoft-specific"></a>Microsoft 專有

Microsoft C 不會限制case **switch** 語句中的值數目。 此數目會受到可用記憶體的限制。 ANSI C 需要在case **switch** 語句中允許至少257標籤。

default適用于 microsoft C 的是已啟用 microsoft 擴充功能。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項可停用這些擴充功能。

## <a name="see-also"></a>另請參閱

[switch語句（c + +）](../cpp/switch-statement-cpp.md)
