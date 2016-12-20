---
title: "is_destructible 類別 | Microsoft Docs"
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
  - "is_destructible"
  - "std.is_destructible"
  - "std::is_destructible"
  - "type_traits/std::is_destructible"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_destructible"
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_destructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為易損壞的。  
  
## 語法  
  
```  
template <class T>  
    struct is_destructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果類型 `T` 是易損壞的類型，則類型述詞的執行個體為 true，否則為 false。 易損壞的類型是指參考類型、物件類型和類型，其中某些類型的 `U` 等於 `remove_all_extents_t<T>`，且未經過評估的運算元 `std::declval<U&>.~U()` 是語式正確的。 不完整的類型、`void` 及函式類型等其他類型，則不屬於易損壞的類型。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)