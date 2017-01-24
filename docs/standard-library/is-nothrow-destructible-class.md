---
title: "is_nothrow_destructible 類別 | Microsoft Docs"
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
  - "is_nothrow_destructible"
  - "std.is_nothrow_destructible"
  - "std::is_nothrow_destructible"
  - "type_traits/std::is_nothrow_destructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_destructible"
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_destructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否的型別是可破壞，解構函式才知道編譯器不會擲回。  
  
## 語法  
  
```  
template <class T>  
    struct is_nothrow_destructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 是可破壞的型別，以及解構函式已知編譯器不會擲回。 否則，它會保留，則為 false。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)