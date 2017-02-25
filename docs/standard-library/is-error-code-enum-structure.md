---
title: "is_error_code_enum 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "future/std::is_error_code_enum"
dev_langs: 
  - "C++"
ms.assetid: 84ae4b99-66d2-41ba-9b50-645fcbe14630
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_error_code_enum 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 [future\_errc](../Topic/future_errc%20Enumeration.md) 的特製化適用於儲存 [error\_code](../standard-library/error-code-class.md)。  
  
## 語法  
  
```  
template<>  
struct is_error_code_enum<Future_errc> : public true_type;  
```  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)