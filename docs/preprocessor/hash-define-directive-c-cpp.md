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
ms.openlocfilehash: b72e2468b9e9984237c81f5cdb3c5691fe95cbd0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216273"
---
# <a name="define-directive-cc"></a>#define 指示詞 (CC++/)

**#Define**會建立一個*宏*, 也就是識別碼或參數化識別碼與權杖字串的關聯。 定義巨集之後，編譯器就可以使用語彙基元字串替代原始程式檔中出現的每個識別項。

## <a name="syntax"></a>語法

> **#define***識別碼* *token-字串*<sub>opt</sub>\
> **#define***識別碼* **(** *identifier*<sub>opt</sub> **,** ... **,** *識別碼*<sub>opt</sub> **)** *token-字串*<sub>opt</sub>

## <a name="remarks"></a>備註

**#Define**指示詞會使編譯器將*標記字串*取代為原始程式檔中每個出現的*識別碼*。 只有在形成權杖時, 才會取代*識別碼*。 也就是說, 如果*識別碼*出現在批註、字串或較長的識別碼中, 則不會取代它。 如需詳細資訊, 請參閱[權杖](../cpp/tokens-cpp.md)。

*Token 字串*引數包含一連串的權杖, 例如關鍵字、常數或完整的語句。 一或多個空白字元必須分隔*識別碼*中的*標記字串*。 這個空白不會視為替代文字的一部分，也不是接在上一個文字語彙基元之後的任何空白。

沒有`#define` *token 字串*的會從來源檔案移除出現的*識別碼*。 此*識別碼*仍會定義, 而且可以使用`#if defined`和`#ifdef`指示詞進行測試。

第二個語法形式會定義類似函式且具有參數的巨集。 這種形式可接受選擇性參數清單，但必須以括號括住。 定義宏之後, 會將每個後續出現的*識別碼*( *identifier*<sub>opt</sub>, ..., *identifier*<sub>opt</sub> ) 取代為具有實際引數的*token 字串*引數版本取代為正式參數。

型式參數名稱會出現在*標記字串*中, 以標記實際值的替代位置。 每個參數名稱可以在*token 字串*中多次出現, 而且名稱可以依任何順序出現。 呼叫中引數的數目必須與巨集定義中參數的數目相符。 盡量使用括號可確保正確解譯複雜的實際引數。

清單中的型式參數是以逗號分隔。 清單中的每個名稱都必須是唯一的，而且清單必須以括號括住。 不能有空格分隔*識別碼*和左括弧。 使用行串連-在分行符號之前加`\`上反斜線 (), 適用于多個原始程式列的長指示詞。 型式參數名稱的範圍會延伸到結束*標記字串*的新行。

如果已在第二種語法形式中定義巨集，則後面接著引數清單的後續文字執行個體會表示巨集呼叫。 在原始程式檔中,*識別碼*實例後面的實際引數, 會符合巨集定義中的對應型式參數。 *Token 字串*中的每個型式參數, 前面不加字串化 (`#`)、字元化 (`#@`) 或標記-貼上 (`##`) 運算子, 或後面`##`沒有運算子, 會取代為對應的實際的引數。 實際引數中的所有巨集都會在指示詞取代型式參數之前展開。 (運算子會在[預處理器運算子](../preprocessor/preprocessor-operators.md)中說明)。

下列具有引數的宏範例說明 **#define**語法的第二種形式:

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

具有副作用的引數有時會造成巨集產生未預期的結果。 指定的型式參數可能會在*token 字串*中出現一次以上。 如果以具有副作用的運算式取代該型式參數，則運算式連同其副作用可能會經過多次求值。 (請參閱[標記-貼上運算子 (# #)](../preprocessor/token-pasting-operator-hash-hash.md)底下的範例)。

`#undef` 指示詞會導致識別碼的前置處理器定義遭到忽略。 如需詳細資訊, 請參閱[#undef](../preprocessor/hash-undef-directive-c-cpp.md)指示詞。

如果要定義的宏名稱會出現在*標記字串*中 (即使是另一個宏展開的結果), 則不會展開。

除非第二個標記序列與第一個相同, 否則具有相同名稱之宏的第二個 **#define**會產生警告。

**Microsoft 專屬**

如果新定義與原始定義在語法上相同，Microsoft C/C++ 可讓您重新定義巨集。 換句話說，這兩個定義可以有不同的參數名稱。 這種行為與 ANSI C 不同, 這需要兩個定義的詞法相同。

例如，下列兩個巨集除了參數名稱之外完全相同。 ANSI C 並不允許這類重新定義, 但是 Microsoft CC++ /會進行編譯, 而不會發生錯誤。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( a1 * a2 )
```

另一方面，下列兩個巨集不相同，而且將會在 Microsoft C/C++ 中產生警告。

```C
#define multiply( f1, f2 ) ( f1 * f2 )
#define multiply( a1, a2 ) ( b1 * b2 )
```

**結束 Microsoft 專屬**

這個範例說明 **#define**指示詞:

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

這會評估為280。

**Microsoft 專屬**

使用[/d](../build/reference/d-preprocessor-definitions.md)編譯器選項定義宏和常數, 與在檔案開頭使用 **#define**前置處理指示詞的效果相同。 使用 /D 選項最多可以定義 30 個巨集。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)
