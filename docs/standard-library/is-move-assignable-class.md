---
title: "is_move_assignable 類別 | Microsoft Docs"
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
  - "is_move_assignable"
  - "std.is_move_assignable"
  - "std::is_move_assignable"
  - "type_traits/std::is_move_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_move_assignable"
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_move_assignable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型可以是移動指派。  
  
## 語法  
  
```  
template<class T>  
    struct is_move_assignable;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 類型是移動指派，如果型別為右值參考可以指派給該型別的參考。 類型述詞相當於 `is_assignable<T&, T&&>`。 移動指派類型包括往返的純量型別，而且有編譯器產生或使用者定義的類別型別移動指派運算子。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)