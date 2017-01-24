---
title: "is_trivially_destructible 類別 | Microsoft Docs"
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
  - "is_trivially_destructible"
  - "std.is_trivially_destructible"
  - "std::is_trivially_destructible"
  - "type_traits/std::is_trivially_destructible"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_destructible"
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_destructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為巨細靡遺地可破壞。  
  
## 語法  
  
```  
template <class T>  
    struct is_trivially_destructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 是可破壞的型別，，編譯器才知道解構函式來使用任何非一般的作業。 否則，它會保留，則為 false。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)