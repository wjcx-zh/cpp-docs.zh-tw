---
title: 函式原型
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: 76e8abdaa2e2d0d8ba14209b45982b6a7f63f2e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227851"
---
# <a name="function-prototypes"></a>函式原型

函式宣告在函式定義之前，並且會指定函式的名稱、傳回型別、儲存類別和其他屬性。 函式宣告也必須建立函式引數的類型和識別項，才能成為原型。

## <a name="syntax"></a>語法

*declaration*宣告：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*宣告規範*屬性-seq*<sub>opt</sub> *init-宣告子-list*<sub>opt</sub> **;**

/\**屬性-seq*<sub>opt</sub>是 Microsoft 特定的\*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-宣告子-list***、***init-* 宣告子    

*init-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;宣告子*declarator* **=***初始化運算式*

宣告*子：*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct*宣告子：/ \* 函式宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **（***參數-類型清單***）**   / \* 新樣式的宣告子      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接*宣告子 **（***識別碼清單*<sub>opt</sub> **）**  / \* 過時樣式的宣告子    \*/

原型的形式與函式定義的相同，但右括號後面加上分號即可終止原型，因此沒有主體。 在任何情況下，傳回類型必須與在函式定義中指定的傳回類型一致。

函式原型有下列重要用途：

- 它們會針對傳回以外類型的函式建立傳回類型 **`int`** 。 雖然傳回值的函式 **`int`** 不需要原型，但建議使用原型。

- 如果沒有完整的原型，就會執行標準轉換，但不會嘗試根據參數數目檢查引數的類型或數目。

- 原型用於在定義這些函式之前初始化函式指標。

- 參數清單用於根據函式定義中的參數檢查函式呼叫中的引數對應。

每個參數的轉換類型決定函式呼叫置於堆疊之引數的解譯方式。 引數和參數之間的類型不符，可能會造成堆疊上的引數解譯不正確。 例如，在16位的電腦上，如果將16位指標當做引數傳遞，然後宣告為 **`long`** 參數，則堆疊上的前32位會被視為 **`long`** 參數。 這個錯誤不只會使用 **`long`** 參數來建立問題，而是使用後面的任何參數。 您可以為所有函式宣告完整的函式原型，來偵測這種錯誤。

原型會建立函式的屬性，以便針對其定義之前 (或發生在其他原始檔案中) 的函式呼叫，檢查引數類型和傳回型別不符的情形。 例如，如果您 **`static`** 在原型中指定儲存類別規範，您也必須在 **`static`** 函式定義中指定儲存類別。

完整的參數宣告（ `int a` ）可以與相同宣告中的抽象宣告子（ **`int`** ）混合。 例如，下列宣告是合法的：

```C
int add( int a, int );
```

原型可以包含以引數傳遞之每個運算式的類型和識別項。 不過，此類識別項的範圍只到宣告結尾為止。 原型也可以反映引數數目可變或未傳遞任何引數這項事實。 若沒有這種清單，就不會顯示不符，因此編譯器無法產生相關的診斷訊息。 如需類型檢查的詳細資訊，請參閱[引數](../c-language/arguments.md)。

現在當使用 **/Za** 編譯器選項進行編譯時，Microsoft C 編譯器中的原型範圍符合 ANSI 標準。 這表示如果您在 **`struct`** **`union`** 原型中宣告或標記，則會在該範圍中輸入標記，而不是在全域範圍中。 例如，為遵循 ANSI 標準而使用 **/Za** 編譯時，若呼叫此函式，一定會出現類型不符錯誤：

```C
void func1( struct S * );
```

若要更正您的程式碼，請在函式原型之前，于全域範圍定義或宣告 **`struct`** 或 **`union`** ：

```C
struct S;
void func1( struct S * );
```

在 **/Ze** 下，仍然會在全域範圍輸入該標記。

## <a name="see-also"></a>另請參閱

[函式](../c-language/functions-c.md)
