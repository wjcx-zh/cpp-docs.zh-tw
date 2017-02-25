---
title: "is_error_condition_enum 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::is_error_condition_enum"
  - "std.is_error_condition_enum"
  - "is_error_condition_enum"
  - "system_error/std::is_error_condition_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_error_condition_enum 類別"
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# is_error_condition_enum 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示型別的述詞 [error\_condition](../standard-library/error-condition-class.md) 列舉型別的測試。  
  
## 語法  
  
```  
template<_Enum>  
    class is_error_condition_enum;  
```  
  
## 備註  
 如果型別是 `_Enum` 列舉型別值套用至存放在 `error_condition`型別，此 [輸入述詞](../standard-library/type-traits.md) 物件執行個體之。  
  
 加入特製化到使用者定義型別的型別是可允許的。  
  
## 需求  
 **標頭**\<系統錯誤\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [\<system\_error\>](../standard-library/system-error.md)