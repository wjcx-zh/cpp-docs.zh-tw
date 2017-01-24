---
title: "is_move_constructible 類別 | Microsoft Docs"
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
  - "is_move_constructible"
  - "std.is_move_constructible"
  - "std::is_move_constructible"
  - "type_traits/std::is_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_move_constructible"
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_move_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有移動建構函式。  
  
## 語法  
  
```  
template <class T>  
    struct is_move_constructible;  
```  
  
#### 參數  
 T  
 要評估的類型  
  
## 備註  
 類型述詞評估為 true 如果型別 `T` 可以建構使用移動作業。 這個述詞相當於 `is_constructible<T, T&&>`。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)