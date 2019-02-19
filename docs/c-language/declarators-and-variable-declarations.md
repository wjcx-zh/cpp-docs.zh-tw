---
title: 宣告子和變數宣告
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147486"
---
# <a name="declarators-and-variable-declarations"></a>宣告子和變數宣告

本節其餘部分將說明在這份清單中摘要說明之變數類型宣告的形式和意義。 特別要提的是，其餘各節將說明如何宣告，如下所示：

|變數類型|描述|
|----------------------|-----------------|
|[簡單變數](../c-language/simple-variable-declarations.md)|使用整數或浮點類型的單一值變數|
|[陣列](../c-language/array-declarations.md)|由具有相同類型之項目集合組成的變數|
|[指標](../c-language/pointer-declarations.md)|指向其他變數並包含變數位置 (採用位址的形式) 而不是值的變數|
|[列舉變數](../c-language/c-enumeration-declarations.md)|具有整數資料類型的簡單變數，其中會保存一個來自一組具名整數常數的值|
|[結構](../c-language/structure-declarations.md)|由值集合所組成的變數可以採用不同的類型。|
|[等位](../c-language/union-declarations.md)|由數個佔用相同儲存空間之不同類型的值所組成的變數|

宣告子是宣告的一部分，用於指定要引入程式的名稱。 它可能包含修飾詞如 <strong>\*</strong> (指標) 和任何 Microsoft 呼叫慣例關鍵字。

**Microsoft 專屬**

在宣告子中

```C
__declspec(thread) char *var;
```

`char` 為類型指定名稱，`__declspec(thread)` 和 `*` 是修飾詞，而 `var` 為識別項的名稱。

**結束 Microsoft 專屬**

您可以使用宣告子來宣告值的陣列、值的指標，以及傳回指定類型值的函式。 宣告子會出現在陣列和指標宣告中，將於本節稍後說明。

## <a name="syntax"></a>語法

*declarator*：<br/>
&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *宣告子*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**

*pointer*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *指標*

*type-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> 如需參考 *declarator* 的語法資訊，請參閱[宣告概觀](../c-language/overview-of-declarations.md)或 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)中的 *declaration* 語法。

當宣告子包含未修改的識別項時，要宣告的項目會具有基底類型。 如果識別碼的左邊出現一個星號 (<strong>\*</strong>)，表示會將類型修改為指標類型。 如果識別碼的後面接著一個方括弧 (**[ ]**)，表示這個類型已修改為陣列類型。 如果識別項的後面接著一個括號，表示這個類型已修改為函式類型。 如需解譯宣告中優先順序的詳細資訊，請參閱[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md)。

每個宣告子至少會宣告一個識別項。 宣告子必須包含類型指定名稱，才是一個完整的宣告。 類型指定名稱會指定陣列類型的元素類型、以指標類型定址的物件類型，或是函式的傳回型別。

[陣列](../c-language/array-declarations.md)和[指標](../c-language/pointer-declarations.md)宣告將於本節中稍後詳細討論。 下列範例說明宣告子的一些簡單形式：

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Microsoft 專屬**

Microsoft C 編譯器並不會限制可修改算術、結構或等位型別的宣告子數目。 這些數目只會受到可用記憶體的限制。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
