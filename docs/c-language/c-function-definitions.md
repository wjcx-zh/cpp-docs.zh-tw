---
title: C 函式定義 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 265dfe599d4c3586b350787baab5977562326991
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757678"
---
# <a name="c-function-definitions"></a>C 函式定義
函式定義會指定函式的名稱、預期收到的參數類型及數目，以及其傳回型別。 函式定義也包括函式主體與其區域變數的宣告，以及決定該函式之行為的陳述式。

## <a name="syntax"></a>語法

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*: /\* 只能於外部 (檔案) 範圍內 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* 是 Microsoft 專有 \*/

原型參數為：

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *宣告*

*declarator*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指標*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* 函式宣告子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)** /\* 新樣式宣告子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)** /\* 過時樣式宣告子 \*/

定義中的參數清單會使用此語法：

*parameter-type-list*: /\* 參數清單 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *宣告子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

舊樣式函式定義中的參數清單會使用此語法：

*identifier-list*: /\* 用於過時的樣式函式定義和宣告 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier-list* **,**  *識別碼*

函式主體的語法為：

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

唯一可以修改函式宣告的儲存類別指定名稱是 **struct** 與 **static**。 **extern** 指定名稱表示可從其他檔案參考該函式；也就是說，會將該函式名稱匯出至連結器。 **static** 指定名稱表示不可從其他檔案參考該函式；亦即，連結器不會匯出名稱。 如果函式定義中不會出現儲存類別，就會假設 **extern**。 在任何情況下，從定義點到檔案結尾都會顯示該函式。

選擇性的 *declaration-specifiers* 和強制性的*宣告子*一起指定函式的傳回類型和名稱。 「宣告子」是為函式命名的識別項組合，函式名稱之後會加上括號。 選擇性的 *attribute-seq* 非終端項是[函式屬性](../c-language/function-attributes.md)中定義的 Microsoft 專有功能。

*direct-declarator* (在*宣告子*語法中) 指定將定義之函式的名稱與其參數的識別項。 如果 *direct-declarator* 包含 *parameter-type-list*，清單會指定所有參數的類型。 這類宣告子也可做為函式原型，以便稍後呼叫函式。

函式定義中 *declaration-list* 的*宣告*不能包含 **register** 以外的 *storage-class-specifier* 。 只有為 **register** 儲存類別指定 **int** 類型的值時，才能忽略 *declaration-specifiers* 語法中的 *type-specifier*。

*compound-statement* 是函式主體，其中包含區域變數宣告、外部宣告項目的參考，以及陳述式。

[函式屬性](../c-language/function-attributes.md)、[儲存類別](../c-language/storage-class.md)、[傳回類型](../c-language/return-type.md)、[參數](../c-language/parameters.md)和[函式主體](../c-language/function-body.md)等節會詳細說明函式定義的元件。

## <a name="see-also"></a>另請參閱
[函式](../c-language/functions-c.md)