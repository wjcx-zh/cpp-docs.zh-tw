---
title: 參數
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipsis (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 57648747bbb50ffe46b199a03563757c331f088a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229567"
---
# <a name="parameters"></a>參數

引數是值的名稱，會由函式呼叫傳遞至函式。 參數是函式預期收到的值。 在函式原型中，函式名稱後面接著的括號會包含函式參數與及類型的完整清單。 參數宣告會指定參數中所儲存值的類型、大小和識別項。

## <a name="syntax"></a>語法

*`function-definition`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`*<sub>opt</sub> *`attribute-seq`*<sub>opt</sub> *`declarator`**`declaration-list`* <sub>opt</sub>*`compound-statement`*

/\**`attribute-seq`* 是 Microsoft 特有的\*/

*`declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`pointer`*<sub>opt</sub>*`direct-declarator`*

*`direct-declarator`*：/ \* 函式宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`direct-declarator`*  **`(`**  *`parameter-type-list`*  **`)`** /\*新樣式的宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`direct-declarator`*  **`(`**  *`identifier-list`*<sub>opt</sub> **`)`**  / opt \*過時樣式的宣告子\*/

*`parameter-type-list`*：/ \* 參數清單\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`, ...`**

*`parameter-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-declaration`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`parameter-list`* **`,`**  *`parameter-declaration`*

*`parameter-declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`* *`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`abstract-declarator`* <sub>opt</sub>

*`parameter-type-list`* 是以逗號分隔的參數宣告序列。 參數清單中每個參數的形式如下所示：

> **`register`**<sub>opt</sub> *`type-specifier`**`declarator`* <sub>opt</sub>

以屬性宣告的函式參數會 **`auto`** 產生錯誤。 參數的識別項會在函式主體中用來參考傳遞至函式的值。 您可以在原型中為參數命名，不過名稱會在宣告結尾超出範圍。 這表示在函式定義中，參數名稱可以用相同方式或不同方式指派。 這些識別碼無法在函式主體的最外層區塊中重新定義，但是它們可以在內部的嵌套區塊中重新定義，如同參數清單是封閉區塊一樣。

中的每個識別碼 *`parameter-type-list`* 前面必須加上適當的類型規範，如下列範例所示：

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

如果參數清單中至少有一個參數出現，則清單的結尾可以是逗號，後面接著三個句點（ **`, ...`** ）。 這種建構稱為「省略符號標記法」，表示函式的可變引數數目。 （如需詳細資訊，請參閱[使用可變數目的引數呼叫](../c-language/calls-with-a-variable-number-of-arguments.md)）。不過，呼叫函式的引數必須至少與最後一個逗號前面的參數數目相同。

如果沒有要傳遞至函式的引數，則參數清單會取代為關鍵字 **`void`** 。 這種用法 **`void`** 有別于其作為類型規範的用法。

參數的順序和類型 (包括使用的省略符號標記法) 在所有函式宣告 (如果有的話) 和函式定義中必須相同。 一般算術轉換之後的引數類型必須與對應參數類型的指派相容。 （如需算術轉換的詳細資訊，請參閱[一般算術轉換](../c-language/usual-arithmetic-conversions.md)）。不會檢查省略號後面的引數。 參數可以具有任何基本、結構、等位、指標或陣列類型。

編譯器會在每個參數和每個引數上分別執行一般算術轉換 (如有需要)。 轉換之後，沒有參數短于 **`int`** ，而且沒有參數具有類型， **`float`** 除非在原型中明確指定參數類型 **`float`** 。 例如，將參數宣告為的效果與將它宣告為 **`char`** 相同 **`int`** 。

## <a name="see-also"></a>另請參閱

[C 函式定義](../c-language/c-function-definitions.md)
