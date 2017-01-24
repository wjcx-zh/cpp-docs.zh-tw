---
title: "error_category 類別 | Microsoft Docs"
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
  - "std::error_category"
  - "system_error/std::error_category"
  - "error_category"
  - "std.error_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_category 類別"
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# error_category 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示抽象、 通用基底物件描述的錯誤代碼的類別。  
  
## 語法  
  
```  
class error_category;  
```  
  
## 備註  
 兩個預先定義的物件實作 `error_category`: [generic\_category](../Topic/generic_category.md) 和 [system\_category](../Topic/system_category.md)。  
  
### TypeDefs  
  
|||  
|-|-|  
|[value\_type](../Topic/error_category::value_type.md)|表示儲存的錯誤代碼值的型別。|  
  
### 成員函式  
  
|||  
|-|-|  
|[default\_error\_condition](../Topic/error_category::default_error_condition.md)|儲存錯誤條件物件的錯誤碼值。|  
|[equivalent](../Topic/error_category::equivalent.md)|傳回值，指定錯誤的物件是否相等。|  
|[訊息](../Topic/error_category::message.md)|傳回指定的錯誤程式碼的名稱。|  
|[name](../Topic/error_category::name.md)|傳回類別的名稱。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_category::operator==.md)|測試是否相等 `error_category` 物件。|  
|[operator\!\=](../Topic/error_category::operator!=.md)|測試是否不等之間 `error_category` 物件。|  
|[operator\<](../Topic/error_category::operator%3C.md)|如果測試 [error\_category](../standard-library/error-category-class.md) 物件是小於 `error_category` 物件傳入以進行比較。|  
  
## 需求  
 **標頭：**\<system\_error\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<system\_error\>](../standard-library/system-error.md)