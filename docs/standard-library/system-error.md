---
title: "&lt;system_error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<system_error>"
  - "std::<system_error>"
  - "<system_error>"
  - "system_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "system_error 標頭"
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;system_error&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含標頭 `<system_error>` 定義例外狀況類別 `system_error` 和處理的低階系統錯誤相關範本。  
  
## 語法  
  
```  
#include <system_error>  
```  
  
### 物件  
  
|||  
|-|-|  
|[generic\_category](../Topic/generic_category.md)|表示錯誤的分類。|  
|[system\_category](../Topic/system_category.md)|代表低階系統溢位造成錯誤的分類。|  
  
### Typedef  
  
|||  
|-|-|  
|[generic\_errno](../Topic/generic_errno.md)|表示列舉型別之任何錯誤程式碼巨集提供符號名稱的型別是由 `<errno.h>`的 Posix 定義。|  
  
### 函式  
  
|||  
|-|-|  
|[make\_error\_code](../Topic/make_error_code.md)|建立 `error_code` 物件。|  
|[make\_error\_condition](../Topic/make_error_condition.md)|建立 `error_condition` 物件。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/operator==%20\(%3Csystem_error%3E\).md)|測試，如果在運算子左方的物件等於右邊的物件。|  
|[operator\!\=](../Topic/operator!=%20\(%3Csystem_error%3E\).md)|測試，如果在運算子左方的物件不等於右邊的物件。|  
|[運算子\<](../Topic/operator%3C%20\(%3Csystem_error%3E\).md)|測試，如果物件小於物件為比較傳遞。|  
  
### 列舉  
  
|||  
|-|-|  
|[errc](../Topic/errc%20Enumeration.md)|做為 `<errno.h>`中的 Posix 定義的錯誤程式碼巨集的符號名稱。|  
  
### 類別和結構。  
  
|||  
|-|-|  
|[error\_category](../standard-library/error-category-class.md)|表示這個摘要，描述錯誤碼類別物件的通用基底。|  
|[error\_code](../standard-library/error-code-class.md)|表示是實作專用的低階系統錯誤。|  
|[error\_condition](../standard-library/error-condition-class.md)|表示使用者定義的錯誤碼。|  
|[is\_error\_code\_enum](../standard-library/is-error-code-enum-class.md)|表示型別的述詞 [error\_code 類別](../standard-library/error-code-class.md) 列舉型別的測試。|  
|[is\_error\_condition\_enum](../standard-library/is-error-condition-enum-class.md)|表示型別的述詞 [error\_condition 類別](../standard-library/error-condition-class.md) 列舉型別的測試。|  
|[system\_error](../standard-library/system-error-class.md)|表示所有例外狀況的基底類別所擲回的報告低階系統溢位。|  
  
## 需求  
 **標頭**\<系統錯誤\>  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)