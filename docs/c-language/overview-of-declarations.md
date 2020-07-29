---
title: 宣告概觀
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 066c0fd307c7562d70c57c31dff23960a6305f2c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217073"
---
# <a name="overview-of-declarations"></a>宣告概觀

「宣告」會指定一組識別項的解譯和屬性。 如果宣告也為以識別項命名的物件或函式保留儲存區，則稱為「定義」。 變數、函式和類型的 C 宣告具有下列語法：

## <a name="syntax"></a>語法

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`attribute-seq`* <sub>opt</sub> *`init-declarator-list`* <sub>opt</sub>**`;`**

/\**`attribute-seq`* <sub>Opt</sub>是 Microsoft 特定的 */

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>opt</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`* **`=`** *`initializer`*

> [!NOTE]
> 的這個語法 *`declaration`* 不會在下列各節中重複。 下列各節中的語法通常會以 *`declarator`* 語法開頭。

中的宣告 *`init-declarator-list`* 包含所要命名的識別碼; *`init`* 是初始化運算式的縮寫。 *`init-declarator-list`* 是以逗號分隔的宣告子序列，其中每一個都可以有額外的類型資訊或初始化運算式，或兩者都有。 包含宣告的 *`declarator`* 識別碼（如果有的話）。 *`declaration-specifiers`* 語法是由類型和儲存類別規範的序列所組成，這些指定名稱會指出連結、儲存持續時間，以及宣告子所代表之實體類型的至少一部分。 宣告是由儲存類別指定名稱、類型規範、類型限定詞、宣告子和初始化運算式的某種組合所組成。

宣告可以包含一或多個中所列的選擇性屬性， *`attribute-seq`* *`seq`* 這是 sequence 的縮寫。 這些 Microsoft 特有的屬性會執行數個功能，這會在本書中詳細討論。

在變數宣告的一般形式中，會 *`type-specifier`* 提供變數的資料類型。 *`type-specifier`* 可以是複合，如同或修改類型時一樣 **`const`** **`volatile`** 。 `declarator` 會為變數命名，可能會修改變數以宣告陣列或指標類型。 例如

```C
int const *fp;
```

宣告名為的變數 `fp` ，做為不可修改（ **`const`** ） **`int`** 值的指標。 若要定義宣告中的多個變數，您可以使用多個宣告子，並以逗號分隔。

一個宣告至少要有一個宣告子，否則其類型規範必須宣告結構標記、等位標記或列舉的成員。 宣告子提供有關識別項的任何其餘資訊。 宣告子是一種識別碼，可以用方括弧（ **`[ ]`** ）、星號（ <strong>`*`</strong> ）或括弧（）加以修改， **`( )`** 分別宣告陣列、指標或函式類型。 當您宣告簡單變數 (例如字元、整數和浮點項目)，或是簡單變數的結構和等位時，`declarator` 就只是識別項。 如需宣告子的詳細資訊，請參閱[宣告子及變數宣告](../c-language/declarators-and-variable-declarations.md)。

所有定義都是隱含的宣告，但並非所有宣告都是定義。 例如，以儲存類別規範開頭的變數宣告 **`extern`** 為「參考」，而不是「定義」宣告。 如果外部變數在定義之前就被參考，或者如果它是在使用它的另一個原始程式檔中定義，則 **`extern`** 需要宣告。 儲存體不是藉由「參考」宣告來配置，也不能在宣告中初始化變數。

變數宣告中需要有儲存類別及/或類型。 除了以外 **`__declspec`** ，宣告中只允許一個儲存類別規範，而且並非所有的儲存類別指定名稱都允許在每個內容中使用。 **`__declspec`** 儲存類別可與其他儲存類別規範搭配使用，且允許超過一次。 宣告的儲存類別規範會影響如何儲存和初始化所宣告的項目，以及程式的哪些部分可以參考該項目。

*`storage-class-specifier`* C 中定義的終端機包括 **`auto`** 、 **`extern`** 、 **`register`** 、 **`static`** 和 **`typedef`** 。 Microsoft C 也包含 *`storage-class-specifier`* 終端機 **`__declspec`** 。 *`storage-class-specifier`* 除了和以外 **`typedef`** 的所有終端 **`__declspec`** 都會在[儲存類別](../c-language/c-storage-classes.md)中討論。 如需的詳細資訊 **`typedef`** ，請參閱宣告[ `typedef` ](../c-language/typedef-declarations.md)。 如需的詳細資訊 **`__declspec`** ，請參閱[擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)。

宣告在原始程式中的位置，以及變數是否有其他宣告存在，都是判定變數存留期的重要因素。 重新宣告可以有好幾個，但定義只有一個。 不過，定義可以出現在多個轉譯單位中。 針對具有內部連結的物件，此規則分別適用於各轉譯單位，因為內部連結的物件對轉譯單位而言是唯一的。 針對具有外部連結的物件，此規則適用於整個程式。 如需可見度的詳細資訊，請參閱[存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)。

類型規範提供識別項資料類型的一些相關資訊。 預設的類型規範是 **`int`** 。 如需詳細資訊，請參閱[類型指定名稱](../c-language/c-type-specifiers.md)。 類型規範也可以定義類型標記、結構和等位元件名稱，以及列舉常數。 如需詳細資訊，請參閱[列舉](../c-language/c-enumeration-declarations.md)宣告、[結構](../c-language/structure-declarations.md)宣告和等位[宣告。](../c-language/union-declarations.md)

有兩個 *`type-qualifier`* 終端機： **`const`** 和 **`volatile`** 。 這些限定詞可指定只有透過左值來存取該類型的物件時，才會相關聯的其他類型屬性。 如需和的詳細資訊 **`const`** **`volatile`** ，請參閱[類型限定詞](../c-language/type-qualifiers.md)。 如需左值定義的詳細資訊，請參閱[左值和右值運算式](../c-language/l-value-and-r-value-expressions.md)。

## <a name="see-also"></a>另請參閱

[C 語言語法摘要](../c-language/c-language-syntax-summary.md)<br/>
[宣告和類型](../c-language/declarations-and-types.md)<br/>
[宣告的摘要](../c-language/summary-of-declarations.md)
