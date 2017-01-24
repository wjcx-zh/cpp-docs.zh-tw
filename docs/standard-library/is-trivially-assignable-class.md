---
title: "is_trivially_assignable 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_trivially_assignable"
  - "std.is_trivially_assignable"
  - "std::is_trivially_assignable"
  - "type_traits/std::is_trivially_assignable"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_assignable"
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_assignable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否為 `From` 類型巨細靡遺地指派給 `To` 類型  
  
## 語法  
  
```  
template <class To, class From>  
    struct is_trivially_assignable;  
```  
  
#### 參數  
 以  
 接收指派的物件類型。  
  
 寄件者  
 提供值的物件類型。  
  
## 備註  
 運算式 `declval<To>() = declval<From>()` 必須是格式正確，而且編譯器必須知道要求任何非一般的作業。 同時 `From` 和 `To` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)