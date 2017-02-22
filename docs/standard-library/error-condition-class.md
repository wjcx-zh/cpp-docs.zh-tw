---
title: "error_condition 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "system_error/std::error_condition"
  - "std::error_condition"
  - "error_condition"
  - "std.error_condition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_condition 類別"
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# error_condition 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示使用者定義的錯誤碼。  
  
## 語法  
  
```  
class error_condition;  
```  
  
## 備註  
 型別 `error_condition` 物件來儲存錯誤代碼值和指標表示用來報告的使用者定義的錯誤的錯誤碼 [分類](../standard-library/error-category-class.md) 的物件。  
  
### 建構函式  
  
|||  
|-|-|  
|[error\_condition](../Topic/error_condition::error_condition.md)|建構屬於 `error_condition` 類型的物件。|  
  
### Typedef  
  
|||  
|-|-|  
|[value\_type](../Topic/error_condition::value_type.md)|代表儲存的錯誤代碼值的型別。|  
  
### 成員函式  
  
|||  
|-|-|  
|[assign](../Topic/error_condition::assign.md)|將錯誤代碼值和分類的錯誤狀況。|  
|[分類](../Topic/error_condition::category.md)|傳回錯誤分類。|  
|[clear](../Topic/error_condition::clear.md)|清除錯誤代碼值和分類。|  
|[message](../Topic/error_condition::message.md)|傳回錯誤碼的名稱。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_condition::operator==.md)|相等的測試在 `error_condition` 物件之間。|  
|[operator\!\=](../Topic/error_condition::operator!=.md)|比較測試在 `error_condition` 物件之間。|  
|[運算子\<](../Topic/error_condition::operator%3C.md)|測試，如果 `error_condition` 物件小於 `error_code` 物件為比較傳遞。|  
|[operator\=](../Topic/error_condition::operator=.md)|指定新的列舉值轉換為 `error_condition` 物件。|  
|[運算子 bool](../Topic/error_condition::operator%20bool.md)|轉換為 `error_condition`型別的變數。|  
  
## 需求  
 **標頭**\<系統錯誤\>  
  
 **命名空間:** std  
  
## 請參閱  
 [error\_category 類別](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)