---
title: "is_nothrow_assignable 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_assignable"
  - "std.is_nothrow_assignable"
  - "std::is_nothrow_assignable"
  - "type_traits/std::is_nothrow_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_assignable"
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_nothrow_assignable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否為 `From` 類型可以指派給 `To` 型別和指派已知不會擲回。  
  
## 語法  
  
```  
template <class To, class From>   
    struct is_nothrow_assignable;  
```  
  
#### 參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## 備註  
 運算式 `declval<To>() = declval<From>()` 必須是格式正確，而且必須知道編譯器不會擲回。 同時 `From` 和 `To` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)