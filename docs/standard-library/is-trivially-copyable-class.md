---
title: "is_trivially_copyable 類別 | Microsoft Docs"
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
  - "is_trivially_copyable"
  - "std.is_trivially_copyable"
  - "std::is_trivially_copyable"
  - "type_traits/std::is_trivially_copyable"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_copyable"
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_copyable 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為巨細靡遺地複製的類型。  
  
## 語法  
  
```  
template<class T>  
    struct is_trivially_copyable;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 是可完整複製類型，否則保留 false。 可完整複製類型會有任何非一般的複製作業、 移動作業或解構函式。 一般而言，複製作業會被視為一般如果當作位元複製。 內建型別和可完整複製類型的陣列是可完整複製。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)