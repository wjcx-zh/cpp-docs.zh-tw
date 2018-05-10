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
ms.openlocfilehash: 69c9846b2ee192071b951d5b9b196d6e4b1968aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="c-function-definitions"></a>C 函式定義
函式定義會指定函式的名稱、預期收到的參數類型及數目，以及其傳回型別。 函式定義也包括函式主體與其區域變數的宣告，以及決定該函式之行為的陳述式。  
  
## <a name="syntax"></a>語法  
 *translation-unit*:  
 *external-declaration*  
  
 *translation-unit external-declaration*  
  
 *external-declaration*: /\* 只能於外部 (檔案) 範圍內 \*/  
 *function-definition*  
  
 `declaration`  
  
 *function-definition*: /\* 這裡的宣告子是函式宣告子 \*/  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* 是 Microsoft 專有 */  
  
 原型參數為：  
  
 *declaration-specifiers*：  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 `declarator`：  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*: /\* 函式宣告子 \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* 新樣式的宣告子 \*/  
  
 *direct-declarator*  **(**  *identifier-list* opt **)** /* 過時樣式宣告子 \*/  
  
 定義中的參數清單會使用此語法：  
  
 *parameter-type-list*: /\* 參數清單 \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *parameter-list*：  
 *parameter-declaration*  
  
 *parameter-list* **,**  *parameter-declaration*  
  
 *parameter-declaration*：  
 *declaration-specifiers declarator*  
  
 *declaration-specifiers abstract declarator* opt  
  
 舊樣式函式定義中的參數清單會使用此語法：  
  
 *identifier-list*: /\* 用於過時的樣式函式定義和宣告 \*/  
 *identifier*  
  
 *identifier-list* **,**  *identifier*  
  
 函式主體的語法為：  
  
 *compound-statement*: /\* 函式主體 \*/  
 **{**  `declaration`-*list* opt*statement-list* opt **}**  
  
 唯一可以修改函式宣告的儲存類別指定名稱是 `extern` 與 **static**。 `extern` 指定名稱表示可從其他檔案參考該函式；也就是說，會將該函式名稱匯出至連結器。 **static** 指定名稱表示不可從其他檔案參考該函式；亦即，連結器不會匯出名稱。 如果函式定義中不會出現儲存類別，就會假設 `extern`。 在任何情況下，從定義點到檔案結尾都會顯示該函式。  
  
 選擇性的 *declaration-specifiers* 和強制性的 `declarator` 一起指定函式的傳回類型和名稱。 `declarator` 是為函式命名的識別項組合，函式名稱之後會加上括號。 選擇性的 *attribute-seq* 非終端項是[函式屬性](../c-language/function-attributes.md)中定義的 Microsoft 專有功能。  
  
 *direct-declarator* (在 `declarator` 語法中) 指定將定義之函式的名稱與其參數的識別項。 如果 *direct-declarator* 包含 *parameter-type-list*，清單會指定所有參數的類型。 這類宣告子也可做為函式原型，以便稍後呼叫函式。  
  
 函式定義 *declaration-list* 中的 `declaration` 不能包含 **register** 以外的 *storage-class-specifier*。 只有為 **register** 儲存類別指定 `int` 類型的值時，才能忽略 *declaration-specifiers* 語法中的 *type-specifier*。  
  
 *compound-statement* 是函式主體，其中包含區域變數宣告、外部宣告項目的參考，以及陳述式。  
  
 [函式屬性](../c-language/function-attributes.md)、[儲存類別](../c-language/storage-class.md)、[傳回類型](../c-language/return-type.md)、[參數](../c-language/parameters.md)和[函式主體](../c-language/function-body.md)等節會詳細說明函式定義的元件。  
  
## <a name="see-also"></a>請參閱  
 [函式](../c-language/functions-c.md)