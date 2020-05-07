---
title: 宣告子和變數宣告
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234514"
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

宣告子是宣告的一部分，用於指定要引入程式的名稱。 它可以包含修飾詞， <strong>\*</strong>例如（指標）和任何 Microsoft 呼叫慣例關鍵字。

**Microsoft 特定的**

在宣告子中

```C
__declspec(thread) char *var;
```

`char` 為類型指定名稱，`__declspec(thread)` 和 `*` 是修飾詞，而 `var` 為識別項的名稱。

**結束 Microsoft 專有**

您可以使用宣告子來宣告值的陣列、值的指標，以及傳回指定類型值的函式。 宣告子會出現在陣列和指標宣告中，將於本節稍後說明。

## <a name="syntax"></a>語法

宣告*子：*<br/>
&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct-* 宣告子：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**（***declarator*宣告子 **）**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **[***常數運算式*<sub>opt</sub> **]**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **（***參數-類型清單***）**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **（***識別碼清單*<sub>opt</sub> **）**    

*指標*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*類型-辨識符號-清單*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*類型-辨識符號-列出*<sub>opt</sub> *指標*

*type-qualifier-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-辨識符號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*類型-辨識符號-清單類型-辨識符號*

> [!NOTE]
> 如需參考 *declarator* 的語法資訊，請參閱[宣告概觀](../c-language/overview-of-declarations.md)或 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)中的 *declaration* 語法。

當宣告子包含未修改的識別項時，要宣告的項目會具有基底類型。 如果識別碼的左邊<strong>\*</strong>出現星號（），則會將類型修改為指標類型。 如果識別碼的後面接著一個方括弧 (**[ ]**)，表示這個類型已修改為陣列類型。 如果識別項的後面接著一個括號，表示這個類型已修改為函式類型。 如需解譯宣告中優先順序的詳細資訊，請參閱[解譯更複雜的宣告子](../c-language/interpreting-more-complex-declarators.md)。

每個宣告子至少會宣告一個識別項。 宣告子必須包含類型指定名稱，才是一個完整的宣告。 類型指定名稱會指定陣列類型的元素類型、以指標類型定址的物件類型，或是函式的傳回型別。

[陣列](../c-language/array-declarations.md)和[指標](../c-language/pointer-declarations.md)宣告將於本節中稍後詳細討論。 下列範例說明宣告子的一些簡單形式：

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Microsoft 特定的**

Microsoft C 編譯器並不會限制可修改算術、結構或等位型別的宣告子數目。 這些數目只會受到可用記憶體的限制。

**結束 Microsoft 專有**

## <a name="see-also"></a>請參閱

[宣告和類型](../c-language/declarations-and-types.md)
