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
ms.openlocfilehash: 5858447602a28dcc5573aa3138e869d106b5aa23
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587371"
---
# <a name="switch-statement-c"></a>`switch`語句（C）

__`switch`__ 和__`case`__ 語句有助於控制複雜的條件式和分支作業。 __`switch`__ 語句會將控制權轉移到其主體中的語句。

## <a name="syntax"></a>語法

> *`selection-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>備註

__`switch`__ 語句會根據的值，讓控制項*`labeled-statement`* 在其語句主體中傳送至其中一個*`expression`*。

*`expression`* 和每個*`constant-expression`* 的值都必須有整數類資料類型。 在*`constant-expression`* 編譯時期，必須有明確的常數整數值。

控制權會傳遞給**`case`** 其*`constant-expression`* 值符合之*`expression`* 值的語句。 __`switch`__ 語句可包含任何數目的__`case`__ 實例。 不過，相同__`switch`__ 語句*`constant-expression`* 內的兩個值都不能有相同的值。 __`switch`__ 語句主體的執行會從相符*`labeled-statement`* 的中的第一個語句開始。 執行會繼續進行，直到主體結束為止，或直到__`break`__ 語句將控制權轉移到主體為止。

使用__`switch`__ 語句通常看起來像這樣：

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

您可以使用__`break`__ 語句來結束處理__`switch`__ 語句內的特定標記語句。 它會分支到__`switch`__ 語句的結尾。 若__`break`__ 沒有，程式會繼續進行下一個標記的語句，執行語句直到__`break`__ 到達或語句結尾為止。 在某些情況下，可能會需要此接續。

如果__`default`__ 沒有任何__`case`__ *`constant-expression`* 值等於的值，則會執行語句*`expression`*。 如果沒有__`default`__ 語句，而且找不到__`case`__ 相符的內容，就不會執行__`switch`__ 主體中的任何語句。 最多隻能有一個__`default`__ 語句。 __`default`__ 語句不一定要放在結尾。 它可能會出現在__`switch`__ 語句主體中的任何位置。 __`case`__ 或__`default`__ 標籤只能出現在__`switch`__ 語句內。

*`expression`* 和__`case`__ 的類型__`switch`__ 必須是*`constant-expression`* 整數。 每個__`case`__ *`constant-expression`* 的值在語句主體中都必須是唯一的。

語句主體的__`case`__ 和__`default`__ 標籤只有在決定在語句主體中開始執行之處的初始測試中才有意義。 __`switch`__ __`switch`__ 語句可以嵌套。 在執行任何__`switch`__ 語句之前，會先初始化任何靜態變數。

> [!NOTE]
> 宣告可以出現在構成__`switch`__ 主體的複合陳述式的開頭，但不會執行包含在宣告中的初始化。 __`switch`__ 語句會將控制權直接傳送至主體內的可執行語句，略過包含初始化的程式列。

下列範例說明__`switch`__ 語句：

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

__`switch`__ 如果`c`等於`'A'`，則會執行此範例中主體的三個語句，因為在下列__`break`__ __`case`__ 之前不會出現任何語句。 執行控制權會轉移到第一個陳述式 (`capital_a++;`)，並且依序繼續執行該主體的其餘部分。 如果 `c` 等於 `'a'`，`letter_a` 和 `total` 會遞增。 只有`total`當不等於`c` `'A'`或`'a'`時，才會遞增。

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

在此範例中， __`break`__ 語句會遵循__`switch`__ 主體的每個語句。 __`break`__ 語句會在執行一個語句之後，強制從語句主體結束。 如果 `i` 等於 -1，則只有 `n` 會遞增。 __`break`__ 下列語句`n++;`會導致執行控制傳遞語句主體，略過其餘語句。 同樣地，如果，`i` 等於 0，只有 `z` 會遞增；如果 `i` 等於 1，只有 `p` 會遞增。 最後__`break`__ 的語句並不是絕對必要的，因為控制權會在複合陳述式的結尾處傳入主體。 其中包含一致性。

單一語句可以包含多個__`case`__ 標籤，如下列範例所示：

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

Microsoft C 不會限制__`case`__ __`switch`__ 語句中的值數目。 此數目會受到可用記憶體的限制。 ANSI C 需要在__`case`__ __`switch`__ 語句中允許至少257標籤。

default適用于 microsoft C 的是已啟用 microsoft 擴充功能。 使用[/za](../build/reference/za-ze-disable-language-extensions.md)編譯器選項可停用這些擴充功能。

## <a name="see-also"></a>另請參閱

[switch語句（c + +）](../cpp/switch-statement-cpp.md)
