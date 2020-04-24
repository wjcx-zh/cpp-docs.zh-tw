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
ms.openlocfilehash: 78ad91ea86d81a3b6d888335ba7b78399a1d2aea
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032066"
---
# <a name="parameters"></a>參數

引數是值的名稱，會由函式呼叫傳遞至函式。 參數是函式預期收到的值。 在函式原型中，函式名稱後面接著的括號會包含函式參數與及類型的完整清單。 參數宣告會指定參數中所儲存值的類型、大小和識別項。

## <a name="syntax"></a>語法

*函數定義*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\**屬性 seq*特定於 Microsoft\*/

*宣告者*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*直接宣告者*:\*/ 函數宣告人\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接宣告型態*  **(**  *參數類型清單*  **)** /\*新式宣告器\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接宣告者*  **(**  *識別子*<sub>清單 ) 選擇</sub> **:** /\*過時式宣告人\*/

*參數型態清單*\*: / 參數清單\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* **, ...**

*參數清單*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數聲明*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* **,**  *參數聲明*

*parameter-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

*parameter-type-list* 是參數宣告的序列，各參數會以逗號分隔。 參數清單中每個參數的形式如下所示：

```C
[register]  type-specifier [declarator]
```

使用 **auto** 屬性宣告的函式參數會產生錯誤。 參數的識別項會在函式主體中用來參考傳遞至函式的值。 您可以在原型中為參數命名，不過名稱會在宣告結尾超出範圍。 因此，參數名稱可以在函式定義中以相同或不同的方式指派。 這些識別項無法在函式主體的最外層區塊中重新定義，但是可以在內部的巢狀區塊中重新定義，如同將參數清單當做封閉區塊一般。

*parameter-type-list* 中的每個識別項前面都必須加上適當的類型指定名稱，如這個範例中所示：

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

如果參數清單中至少有一個參數,則清單可以以逗號結尾,後跟三個句點 **(...)。** 此構造稱為"省略表示法",表示函數的參數數可變。 (有關詳細資訊[,請參閱具有可變數的呼叫](../c-language/calls-with-a-variable-number-of-arguments.md)。但是,對函數的調用必須具有至少與最後一個逗號之前的參數相同的參數數。

如果沒有要傳遞至函式的引數，則參數清單會以關鍵字 `void` 取代。 這種 `void` 用法與其做為類型指定名稱的用法不同。

參數的順序和類型 (包括使用的省略符號標記法) 在所有函式宣告 (如果有的話) 和函式定義中必須相同。 一般算術轉換之後的引數類型必須與對應參數類型的指派相容。 (有關算術轉換的資訊,請參閱[常用的字轉換](../c-language/usual-arithmetic-conversions.md)。不會檢查省略號之後的參數。 參數可以具有任何基本、結構、等位、指標或陣列類型。

編譯器會在每個參數和每個引數上分別執行一般算術轉換 (如有需要)。 在轉換之後，參數的長度不會比 `int` 短，而且除非參數類型在原型中明確指定為 **float**，否則參數不會具有 **float** 類型。 這表示，例如將一個參數宣告為 `char` 的效果與將它宣告為 `int` 的效果相同。

## <a name="see-also"></a>另請參閱

[C 函數定義](../c-language/c-function-definitions.md)
