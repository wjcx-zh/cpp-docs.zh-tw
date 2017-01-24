---
title: "is_assignable 類別 | Microsoft Docs"
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
  - "is_assignable"
  - "std.is_assignable"
  - "std::is_assignable"
  - "type_traits/std::is_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_assignable"
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_assignable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否為 `From` 類型可以指派給 `To` 型別。  
  
## 語法  
  
```  
template <class To, class From>  
    struct is_assignable;  
```  
  
#### 參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## 備註  
 未評估的運算式 `declval<To>() = declval<From>()` 必須是格式正確。 同時 `From` 和 `To` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)