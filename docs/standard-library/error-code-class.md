---
title: "error_code 類別 | Microsoft Docs"
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
  - "error_code"
  - "std.error_code"
  - "std::error_code"
  - "system_error/std::error_code"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_code 類別"
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# error_code 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示是實作專用的低階系統錯誤。  
  
## 語法  
  
```  
class error_code;  
```  
  
## 備註  
 型別 `error_code` 類別物件來儲存錯誤代碼值和指標表示錯誤碼 [分類](../standard-library/error-category-class.md) 所報告的低階系統錯誤的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[error\_code](../Topic/error_code::error_code.md)|建構屬於 `error_code` 類型的物件。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/error_code::value_type.md)|代表儲存的錯誤代碼值的型別。|  
  
### 成員函式  
  
|||  
|-|-|  
|[assign](../Topic/error_code::assign.md)|將錯誤代碼值和分類為錯誤碼。|  
|[分類](../Topic/error_code::category.md)|傳回錯誤分類。|  
|[clear](../Topic/error_code::clear.md)|清除錯誤代碼值和分類。|  
|[default\_error\_condition](../Topic/error_code::default_error_condition.md)|傳回預設錯誤條件。|  
|[message](../Topic/error_code::message.md)|傳回錯誤碼的名稱。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_code::operator==.md)|相等的測試在 `error_code` 物件之間。|  
|[operator\!\=](../Topic/error_code::operator!=.md)|比較測試在 `error_code` 物件之間。|  
|[運算子\<](../Topic/error_code::operator%3C.md)|測試，如果 `error_code` 物件小於 `error_code` 物件為比較傳遞。|  
|[operator\=](../Topic/error_code::operator=.md)|指定新的列舉值轉換為 `error_code` 物件。|  
|[運算子 bool](../Topic/error_code::operator%20bool.md)|轉換為 `error_code`型別的變數。|  
  
## 需求  
 **標頭**\<系統錯誤\>  
  
 **命名空間:** std  
  
## 請參閱  
 [error\_category 類別](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)