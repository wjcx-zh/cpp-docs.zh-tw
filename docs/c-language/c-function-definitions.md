---
title: C 函式定義
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: a26f95f8fef2b52dac36dd5d33f826c73fd84eee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228007"
---
# <a name="c-function-definitions"></a>C 函式定義

函式定義會指定函式的名稱、預期收到的參數類型及數目，以及其傳回型別。 函式定義也包括函式主體與其區域變數的宣告，以及決定該函式之行為的陳述式。

## <a name="syntax"></a>語法

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*外部宣告* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*外部*宣告：/ \* 僅允許在外部（檔案）範圍\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*函式定義*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*清點*

*函式定義*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\**屬性-seq*是 Microsoft 特有的\*/

原型參數為：

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*清點*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *宣告*

宣告*子：*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct*宣告子：/ \* 函式宣告子\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-* 宣告子 **（***參數-類型清單***）**  / \* 新樣式的宣告子      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*直接*宣告子 **（***識別碼清單*<sub>opt</sub> **）**  / \* 過時樣式的宣告子    \*/

定義中的參數清單會使用此語法：

*參數-類型-清單*：/ \* 參數清單\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數清單* **，...**

*參數清單*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*參數-清單* **、***參數*宣告  

*parameter-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

舊樣式函式定義中的參數清單會使用此語法：

*identifier-list*：/ \* 用於過時樣式的函式定義和宣告\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼-清單* **、**  *識別碼*

函式主體的語法為：

*複合陳述式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{宣告** *-列出*<sub>opt</sub> *語句清單*<sub>opt</sub> **}**

唯一可以修改函式宣告的儲存類別指定名稱是 **`extern`** 和 **`static`** 。 **`extern`** 規範表示可以從其他檔案參考該函式; 也就是說，函數名稱會匯出至連結器。 **`static`** 規範表示無法從其他檔案參考該函式; 也就是說，連結器不會匯出該名稱。 如果函式定義中沒有出現任何儲存類別， **`extern`** 則會假設為。 在任何情況下，從定義點到檔案結尾都會顯示該函式。

選擇性的 *declaration-specifiers* 和強制性的*宣告子*一起指定函式的傳回類型和名稱。 「宣告子」** 是為函式命名的識別項組合，函式名稱之後會加上括號。 選擇性的 *attribute-seq* 非終端項是[函式屬性](../c-language/function-attributes.md)中定義的 Microsoft 專有功能。

*direct-declarator* (在*宣告子*語法中) 指定將定義之函式的名稱與其參數的識別項。 如果 *direct-declarator* 包含 *parameter-type-list*，清單會指定所有參數的類型。 這類宣告子也可做為函式原型，以便稍後呼叫函式。

函式定義中宣告*清單**內的*宣告不能包含以外的*儲存類別規範* **`register`** 。 只有在為類型的值指定了儲存類別*時，才*可以省略宣告規範語法中的*型別（type）* **`register`** **`int`** 。

*compound-statement* 是函式主體，其中包含區域變數宣告、外部宣告項目的參考，以及陳述式。

[函式屬性](../c-language/function-attributes.md)、[儲存類別](../c-language/storage-class.md)、[傳回類型](../c-language/return-type.md)、[參數](../c-language/parameters.md)和[函式主體](../c-language/function-body.md)等節會詳細說明函式定義的元件。

## <a name="see-also"></a>另請參閱

[函式](../c-language/functions-c.md)
