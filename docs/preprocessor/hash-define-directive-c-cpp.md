---
title: '#define 指示詞 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#define'
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
ms.openlocfilehash: e9e5b7a02ee55c05aa44278fbceb9c42f372c443
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506672"
---
# <a name="define-directive-cc"></a>#define 指示詞 (C/c + +) 

**#Define**會建立*宏*，也就是識別碼或參數化識別碼與標記字串的關聯。 定義巨集之後，編譯器就可以使用語彙基元字串替代原始程式檔中出現的每個識別項。

## <a name="syntax"></a>Syntax

> **#define** *識別碼* *token-字串*<sub>opt</sub>\
> **#define** *識別碼* ** (** * *<sub>選擇</sub>**,** 識別碼 **，** *識別碼*<sub>opt</sub> **) ** *token-字串*<sub>opt</sub>

## <a name="remarks"></a>備註

**#Define**指示詞會使編譯器以*標記字串*取代原始程式檔中每個出現的*識別碼*。 只有在形成權杖時，才會取代 *識別碼* 。 亦即，如果 *識別碼* 出現在批註、字串中或較長識別碼的一部分，則不會取代。 如需詳細資訊，請參閱 [權杖](../cpp/character-sets.md)。

*Token 字串*引數包含一連串的 token，例如關鍵字、常數或完整語句。 一或多個空白字元必須分隔 *標記字串* 與 *識別碼*。 這個空白不會視為替代文字的一部分，也不是接在上一個文字語彙基元之後的任何空白。

`#define`沒有*權杖字串*的會從原始程式檔中移除出現的*識別碼*。 *識別碼*仍會保持定義，並且可以使用和指示詞進行測試 `#if defined` `#ifdef` 。

第二個語法形式會定義類似函式且具有參數的巨集。 這種形式可接受選擇性參數清單，但必須以括號括住。 定義宏之後，每個後續出現的 *識別碼* ( *識別碼*<sub>opt</sub>、...、 *識別碼*<sub>opt</sub> ) 都會取代為具有實作為型式參數之實值的 *權杖字串* 引數版本。

型式參數名稱會出現在 *token 字串* 中，以標示實際值的替代位置。 每個參數名稱可以出現在 *標記字串*中多次，且名稱可以依任何順序出現。 呼叫中引數的數目必須與巨集定義中參數的數目相符。 盡量使用括號可確保正確解譯複雜的實際引數。

清單中的型式參數是以逗號分隔。 清單中的每個名稱都必須是唯一的，而且清單必須以括號括住。 沒有空格可分隔 *識別碼* 和左括弧。 使用行串連： `\` 在多個原始程式列上，將反斜線 () 緊接在換行字元前面）。 型式參數名稱的範圍會延伸到結束 *權杖字串*的新行。

如果已在第二種語法形式中定義巨集，則後面接著引數清單的後續文字執行個體會表示巨集呼叫。 在原始程式檔中的 *識別碼* 實例之後的實際引數，會與巨集定義中的對應型式參數相符。 Token 字串中的每個 *型式* 參數（前面不是字串化 (`#`) 、字元化 (`#@`) 或標記貼 `##` 上 () 運算子（或後面不是 `##` 運算子）都會由對應的實際引數取代。 實際引數中的所有巨集都會在指示詞取代型式參數之前展開。  (運算子會在 [預處理器運算子](../preprocessor/preprocessor-operators.md)中說明。 ) 

下列具有引數的宏範例說明 **#define** 語法的第二種形式：

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

具有副作用的引數有時會造成巨集產生未預期的結果。 給定的型式參數可能會在 *標記字串*中出現一次以上。 如果以具有副作用的運算式取代該型式參數，則運算式連同其副作用可能會經過多次求值。  (請參閱標記貼上 [運算子 ( # # ) ](../preprocessor/token-pasting-operator-hash-hash.md)的範例。 ) 

`#undef` 指示詞會導致識別碼的前置處理器定義遭到忽略。 如需詳細資訊，請參閱 [#undef](../preprocessor/hash-undef-directive-c-cpp.md) 指示詞。

如果所定義的宏名稱發生在 *token 字串* (中，即使是另一個宏展開) 的結果，也不會展開。

除非第二個權杖順序與第一個相同，否則相同名稱之宏的第二個 **#define** 會產生警告。

**Microsoft 特定的**

如果新定義與原始定義在語法上相同，Microsoft C/C++ 可讓您重新定義巨集。 換句話說，這兩個定義可以有不同的參數名稱。 這種行為與 ANSI C 不同，這需要兩個定義在詞法上相同。

例如，下列兩個巨集除了參數名稱之外完全相同。 ANSI C 不允許這類重新定義，但 Microsoft C/c + + 會進行編譯而不會發生錯誤。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

另一方面，下列兩個巨集不相同，而且將會在 Microsoft C/C++ 中產生警告。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**結束 Microsoft 專有**

此範例說明 **#define** 指示詞：

```C
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```

第一個陳述式會將識別項 `WIDTH` 定義為整數常數 80，並根據 `LENGTH` 定義 `WIDTH` 和整數常數 10。 出現的每個 `LENGTH` 都會由 (`WIDTH + 10`) 取代。 然後出現的每個 `WIDTH + 10` 都會依序由運算式 (`80 + 10`) 取代。 `WIDTH + 10` 前後的括號很重要，因為括號可用於控制陳述式中的解譯方式，如下所示：

```C
var = LENGTH * 20;
```

在前置處理階段之後，陳述式會變成：

```C
var = ( 80 + 10 ) * 20;
```

該陳述式的判斷值為 1800。 若沒有括號，則結果為：

```C
var = 80 + 10 * 20;
```

它會評估為280。

**Microsoft 特定的**

使用 [/d](../build/reference/d-preprocessor-definitions.md) 編譯器選項定義宏和常數的效果，與在檔案開頭使用 **#define** 前置處理指示詞相同。 使用 /D 選項最多可以定義 30 個巨集。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)
