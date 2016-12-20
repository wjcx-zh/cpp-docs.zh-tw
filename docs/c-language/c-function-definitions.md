---
title: "C 函式定義 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "宣告子, 函式"
  - "宣告函式, 關於函式宣告"
  - "宣告函式, 宣告子"
  - "宣告函式, 變數"
  - "函式主體"
  - "函式宣告子"
  - "函式定義"
  - "函式參數, 函式定義"
  - "函式 [C], 參數"
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 函式定義
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

函式定義會指定函式的名稱、預期收到的參數類型及數目，以及其傳回類型。  函式定義也包括函式主體與其區域變數的宣告，以及決定該函式之行為的陳述式。  
  
## 語法  
 *translation\-unit*：  
 *外部宣告*  
  
 *轉譯單位外部宣告*  
  
 *external\-declaration*: \/\* 僅可用於外部 \(檔案\) 範圍 \*\/  
 *函式定義*  
  
 `declaration`  
  
 *function\-definition*: \/\* 這裡的宣告子是函式宣告子 \*\/  
 *declaration\-specifiers*  opt *attribute\-seq* opt *declarator declaration\-list* opt *compound\-statement*  
  
 \/\* *attribute\-seq* 是 Microsoft 專有 \*\/  
  
 原型參數為：  
  
 *declaration\-specifiers*：  
 *storage\-class\-specifier declaration\-specifiers*  opt  
  
 *type\-specifier declaration\-specifiers*  opt  
  
 *type\-qualifier declaration\-specifiers*  opt  
  
 *declaration\-list*：  
 *宣告*  
  
 *declaration\-list 宣告*  
  
 `declarator`:  
 *pointer*  opt *direct\-declarator*  
  
 *direct\-declarator*: \/\* 函式宣告子 \*\/  
 *direct\-declarator*  **\(**  *parameter\-type\-list*  **\)** \/\* 新樣式宣告子 \*\/  
  
 *direct\-declarator*  **\(**  *identifier\-list*  opt **\)** \/\* 過時樣式宣告子 \*\/  
  
 定義中的參數清單會使用此語法：  
  
 *parameter\-type\-list*: \/\* 參數清單 \*\/  
 *parameter\-list*  
  
 *parameter\-list* **, ...**  
  
 *parameter\-list*:  
 *參數宣告*  
  
 *parameter\-list* **,**  *parameter\-declaration*  
  
 *parameter\-declaration*:  
 *declaration\-specifiers declarator*  
  
 *declaration\-specifiers abstract declarator*  opt  
  
 舊樣式函式定義中的參數清單會使用此語法：  
  
 *identifier\-list*: \/\* 用於過時的樣式函式定義和宣告 \*\/  
 *識別項*  
  
 *identifier\-list* **、** *identifier*  
  
 函式主體的語法為：  
  
 *compound\-statement*: \/\* 函式主體 \*\/  
 **{**  `declaration`\-*list* opt *statement\-list* opt **}**  
  
 唯一可以修改函式宣告的儲存類別指定名稱是 `extern` 和 **static**。  `extern` 指定名稱表示可從其他檔案參考該函式；也就是說，會將該函式名稱匯出至連結器。  **static** 指定名稱表示不可從其他檔案參考該函式；也就是說，連結器不會匯出名稱。  如果函式定義中不會出現儲存類別，就會假設 `extern`。  在任何情況下，從定義點到檔案結尾都會顯示該函式。  
  
 選擇性的 *declaration\-specifiers* 和強制性的 `declarator` 一起指定函式的傳回類型和名稱。  `declarator` 是為函式命名的識別項組合，函式名稱之後會加上括號。  選擇性的 *attribute\-seq* 非終端是[函式屬性](../c-language/function-attributes.md)中定義的 Microsoft 專有功能。  
  
 *direct\-declarator* \(在 `declarator` 語法中\) 指定將定義之函式的名稱及其參數的識別項。  如果 *direct\-declarator* 包含 *parameter\-type\-list*，清單會指定所有參數的類型。  這類宣告子也可做為函式原型，以便稍後呼叫函式。  
  
 除了 **register** 之外，函式定義中 *declaration\-list* 的 `declaration` 不能包含 *storage\-class\-specifier*。  只有指定 `int` 類型的值的**register** 儲存類別時，才能忽略 *declaration\-specifiers* 語法中的 *type\-specifier*。  
  
 *compound\-statement* 是函式主體，其中包含區域變數宣告、外部宣告項目的參考，以及陳述式。  
  
 [函式屬性](../c-language/function-attributes.md)、[儲存類別](../c-language/storage-class.md)、[傳回類型](../c-language/return-type.md)、[參數](../c-language/parameters.md)和[函式主體](../c-language/function-body.md)等節會詳細說明函式定義的元件。  
  
## 請參閱  
 [函式](../c-language/functions-c.md)