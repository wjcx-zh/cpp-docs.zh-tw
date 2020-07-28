---
title: :::no-loc(switch):::語句（C）
ms.date: 04/25/2020
f1_keywords:
- ':::no-loc(switch):::'
helpviewer_keywords:
- ':::no-loc(switch)::: keyword [C]'
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- ':::no-loc(switch):::'
- ':::no-loc(case):::'
- ':::no-loc(default):::'
- ':::no-loc(break):::'
ms.openlocfilehash: bdd6885f67728a3c81e395f05c33191156896ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220778"
---
# <a name="no-locswitch-statement-c"></a>`:::no-loc(switch):::`語句（C）

**`:::no-loc(switch):::`** 和 **`:::no-loc(case):::`** 語句有助於控制複雜的條件式和分支作業。 語句會將 **`:::no-loc(switch):::`** 控制權轉移到其主體中的語句。

## <a name="syntax"></a>語法

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(switch)::: (`**&nbsp;*`expression`* &nbsp;**`)`**&nbsp;*`statement`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(case):::`**&nbsp;*`constant-expression`*&nbsp;**`:`**&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; **`:::no-loc(default):::`**&nbsp;**`:`**&nbsp;*`statement`*

## <a name="remarks"></a>備註

**`:::no-loc(switch):::`** 語句會 *`labeled-statement`* 根據的值，讓控制項在其語句主體中傳送至其中一個 *`expression`* 。

*`expression`* 和每個的值都 *`constant-expression`* 必須有整數類資料類型。 *`constant-expression`* 在編譯時期，必須有明確的常數整數值。

控制權會傳遞給 **`:::no-loc(case):::`** 其 *`constant-expression`* 值符合之值的語句 *`expression`* 。 **`:::no-loc(switch):::`** 語句可包含任何數目的 **`:::no-loc(case):::`** 實例。 不過，相同語句內的兩個值都不 *`constant-expression`* **`:::no-loc(switch):::`** 能有相同的值。 語句主體的執行會從 **`:::no-loc(switch):::`** 相符的中的第一個語句開始 *`labeled-statement`* 。 執行會繼續進行，直到主體結束為止，或直到 **`:::no-loc(break):::`** 語句將控制權轉移到主體為止。

使用 **`:::no-loc(switch):::`** 語句通常看起來像這樣：

```C
:::no-loc(switch)::: ( expression )
{
    // declarations
    // . . .
    :::no-loc(case)::: constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        :::no-loc(break):::;
    :::no-loc(default)::::
        // statements executed if expression does not equal
        // any :::no-loc(case)::: constant_expression
}
```

您可以使用 **`:::no-loc(break):::`** 語句來結束處理語句內的特定標記語句 **`:::no-loc(switch):::`** 。 它會分支到語句的結尾 **`:::no-loc(switch):::`** 。 **`:::no-loc(break):::`** 若沒有，程式會繼續進行下一個標記的語句，執行語句直到 **`:::no-loc(break):::`** 到達或語句結尾為止。 在某些情況下，可能會需要此接續。

**`:::no-loc(default):::`** 如果沒有任何 **`:::no-loc(case):::`** *`constant-expression`* 值等於的值，則會執行語句 *`expression`* 。 如果沒有 **`:::no-loc(default):::`** 語句，而且找不到 **`:::no-loc(case):::`** 相符的內容，就不會執行主體中的任何語句 **`:::no-loc(switch):::`** 。 最多隻能有一個 **`:::no-loc(default):::`** 語句。 **`:::no-loc(default):::`** 語句不一定要放在結尾。 它可能會出現在語句主體中的任何位置 **`:::no-loc(switch):::`** 。 **`:::no-loc(case):::`** 或 **`:::no-loc(default):::`** 標籤只能出現在語句內 **`:::no-loc(switch):::`** 。

和的類型 **`:::no-loc(switch):::`** *`expression`* **`:::no-loc(case):::`** *`constant-expression`* 必須是整數。 每個的值在 **`:::no-loc(case):::`** *`constant-expression`* 語句主體中都必須是唯一的。

**`:::no-loc(case):::`** **`:::no-loc(default):::`** 語句主體的和標籤 **`:::no-loc(switch):::`** 只有在決定在語句主體中開始執行之處的初始測試中才有意義。 **`:::no-loc(switch):::`** 語句可以嵌套。 在執行任何語句之前，會先初始化任何靜態變數 **`:::no-loc(switch):::`** 。

> [!NOTE]
> 宣告可以出現在構成主體的複合陳述式的開頭 **`:::no-loc(switch):::`** ，但不會執行包含在宣告中的初始化。 **`:::no-loc(switch):::`** 語句會將控制權直接傳送至主體內的可執行語句，略過包含初始化的程式列。

下列範例說明 **`:::no-loc(switch):::`** 語句：

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'A':
        capital_a++;
    :::no-loc(case)::: 'a':
        letter_a++;
    :::no-loc(default)::: :
        total++;
}
```

**`:::no-loc(switch):::`** 如果等於，則會執行此範例中主體的三個語句 `c` `'A'` ，因為在 **`:::no-loc(break):::`** 下列之前不會出現任何語句 **`:::no-loc(case):::`** 。 執行控制權會轉移到第一個陳述式 (`capital_a++;`)，並且依序繼續執行該主體的其餘部分。 如果 `c` 等於 `'a'`，`letter_a` 和 `total` 會遞增。 只有 `total` 當不等於或時，才會遞增 `c` `'A'` `'a'` 。

```C
:::no-loc(switch):::( i )
{
    :::no-loc(case)::: -1:
        n++;
        :::no-loc(break):::;
    :::no-loc(case)::: 0 :
        z++;
        :::no-loc(break):::;
    :::no-loc(case)::: 1 :
        p++;
        :::no-loc(break):::;
}
```

在此範例中， **`:::no-loc(break):::`** 語句會遵循主體的每個語句 **`:::no-loc(switch):::`** 。 **`:::no-loc(break):::`** 語句會在執行一個語句之後，強制從語句主體結束。 如果 `i` 等於 -1，則只有 `n` 會遞增。 **`:::no-loc(break):::`** 下列語句 `n++;` 會導致執行控制傳遞語句主體，略過其餘語句。 同樣地，如果，`i` 等於 0，只有 `z` 會遞增；如果 `i` 等於 1，只有 `p` 會遞增。 最後的 **`:::no-loc(break):::`** 語句並不是絕對必要的，因為控制權會在複合陳述式的結尾處傳入主體。 其中包含一致性。

單一語句可以包含多個 **`:::no-loc(case):::`** 標籤，如下列範例所示：

```C
:::no-loc(switch):::( c )
{
    :::no-loc(case)::: 'a' :
    :::no-loc(case)::: 'b' :
    :::no-loc(case)::: 'c' :
    :::no-loc(case)::: 'd' :
    :::no-loc(case)::: 'e' :
    :::no-loc(case)::: 'f' :  convert_hex(c);
}
```

在此範例中，如果 *constant-expression* 等於 `'a'` 與 `'f'` 之間的任何字母，則會呼叫 `convert_hex` 函式。

### <a name="microsoft-specific"></a>Microsoft 專有

Microsoft C 不會限制 **`:::no-loc(case):::`** 語句中的值數目 **`:::no-loc(switch):::`** 。 此數目會受到可用記憶體的限制。 ANSI C 需要在 **`:::no-loc(case):::`** 語句中允許至少257標籤 **`:::no-loc(switch):::`** 。

:::no-loc(default):::適用于 Microsoft C 的是已啟用 microsoft 擴充功能。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項可停用這些擴充功能。

## <a name="see-also"></a>另請參閱

[:::no-loc(switch):::語句（c + +）](../cpp/:::no-loc(switch):::-statement-cpp.md)
