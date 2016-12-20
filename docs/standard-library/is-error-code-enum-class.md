---
title: "is_error_code_enum 類別 | Microsoft Docs"
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
  - "system_error/std::is_error_code_enum"
  - "std.is_error_code_enum"
  - "is_error_code_enum"
  - "std::is_error_code_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_error_code_enum 類別"
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_error_code_enum 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示型別的述詞 [error\_code](../standard-library/error-code-class.md) 列舉型別的測試。  
  
## 語法  
  
```  
template<_Enum>  
    class is_error_code_enum;  
```  
  
## 備註  
 如果型別是 `_Enum` 列舉型別值套用至存放在 `error_code`型別，此 [輸入述詞](../standard-library/type-traits.md) 物件執行個體之。  
  
 加入特製化到使用者定義型別的型別是可允許的。  
  
## 需求  
 **標頭**\<系統錯誤\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [\<system\_error\>](../standard-library/system-error.md)