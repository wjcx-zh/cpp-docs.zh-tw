---
title: '#define 指示詞 （C/c + +） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#define'
dev_langs:
- C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e24c7e020f0008a78d4595577c656003bad359c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765677"
---
# <a name="define-directive-cc"></a>#define 指示詞 (C/C++)

**#Define**會建立*巨集*，這是識別項或參數化識別項與語彙基元字串的關聯。 定義巨集之後，編譯器就可以使用語彙基元字串替代原始程式檔中出現的每個識別項。

## <a name="syntax"></a>語法

`#define` *識別項**語彙基元字串*<sub>選擇</sub>

`#define` *識別項* `(` *識別項*<sub>選擇</sub>`,` *...* `,` *識別項*<sub>選擇</sub>`)` *語彙基元字串*<sub>選擇</sub>

## <a name="remarks"></a>備註

**#Define**指示詞可讓編譯器替代*語彙基元字串*出現的每個*識別碼*原始程式檔中。 *識別碼*只有當它在形成語彙基元時，才會被取代。 亦即*識別碼*不被取代，如果它出現在註解，在字串中，或做為較長的識別項的一部分。 如需詳細資訊，請參閱 <<c0> [ 語彙基元](../cpp/tokens-cpp.md)。

*語彙基元字串*引數包含一連串的語彙基元，例如關鍵字、 常數或完整的陳述式。 一或多個空格字元必須分隔*語彙基元字串*從*識別項*。 這個空白不會視為替代文字的一部分，也不是接在上一個文字語彙基元之後的任何空白。

A`#define`而不需要*語彙基元字串*移除的項目*識別碼*從原始程式檔。 *識別碼*仍然定義，而且可以使用測試`#if defined`和`#ifdef`指示詞。

第二個語法形式會定義類似函式且具有參數的巨集。 這種形式可接受選擇性參數清單，但必須以括號括住。 巨集的定義，每個後續相符項目後*識別碼*(*識別項*<sub>選擇</sub>，...，*識別碼*<sub>opt</sub> ) 的版本會取代*語彙基元字串*實際引數替代型式參數的引數。

型式參數名稱會出現在*語彙基元字串*來標記的實際值來取代其中的位置。 每個參數名稱可以在中出現多次*語彙基元字串*，且名稱可依任何順序出現。 呼叫中引數的數目必須與巨集定義中參數的數目相符。 盡量使用括號可確保正確解譯複雜的實際引數。

清單中的型式參數是以逗號分隔。 清單中的每個名稱都必須是唯一的，而且清單必須以括號括住。 任何空格分隔*識別碼*和左括號。 使用行串連，放置一個反斜線 (`\`) 新行字元正前方的多個來源行的長指示詞。 型式參數名稱的範圍會延伸到新的一行，結束*語彙基元字串*。

如果已在第二種語法形式中定義巨集，則後面接著引數清單的後續文字執行個體會表示巨集呼叫。 接下來的執行個體的實際引數*識別碼*原始程式檔中就會對應到在巨集定義中對應的型式參數。 在每個型式參數*語彙基元字串*會未加上字串化運算子 (`#`)、 字元化運算子 (`#@`)，或語彙基元帶入 (`##`) 運算子，或者後面沒有`##`運算子，取代為對應的實質引數。 實際引數中的所有巨集都會在指示詞取代型式參數之前展開。 (運算子所述[前置處理器運算子](../preprocessor/preprocessor-operators.md)。)

使用引數的巨集的下列範例說明第二個形式 **#define**語法：

```C
// Macro to define cursor lines
#define CURSOR(top, bottom) (((top) << 8) | (bottom))

// Macro to get a random integer with a specified range
#define getrandom(min, max) \
    ((rand()%(int)(((max) + 1)-(min)))+ (min))
```

具有副作用的引數有時會造成巨集產生未預期的結果。 指定的型式參數可能會出現一個以上的時間，以*語彙基元字串*。 如果以具有副作用的運算式取代該型式參數，則運算式連同其副作用可能會經過多次求值。 (請參閱底下的範例[語彙基元帶入的運算子 （# #）](../preprocessor/token-pasting-operator-hash-hash.md)。)

`#undef` 指示詞會導致識別碼的前置處理器定義遭到忽略。 請參閱[#undef 指示詞](../preprocessor/hash-undef-directive-c-cpp.md)如需詳細資訊。

如果所定義的巨集的名稱會發生*語彙基元字串*（甚至是另一個巨集展開），因為它不會擴展。

第二個 **#define**巨集具有相同名稱會產生警告，除非第二個語彙基元序列與第一個。

**Microsoft 專屬**

如果新定義與原始定義在語法上相同，Microsoft C/C++ 可讓您重新定義巨集。 換句話說，這兩個定義可以有不同的參數名稱。 此行為不同於 ANSI C 中，這需要兩個的定義在語彙上完全相同。

例如，下列兩個巨集除了參數名稱之外完全相同。 ANSI C 不允許這類重新定義，但 Microsoft C/c + + 所編譯的是它不會發生錯誤。

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

此範例說明 **#define**指示詞：

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

這會評估為 280。

**Microsoft 專屬**

定義巨集和常數[/D](../build/reference/d-preprocessor-definitions.md)編譯器選項都有使用相同的效果 **#define**前置處理器指示詞檔案的開頭。 使用 /D 選項最多可以定義 30 個巨集。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)