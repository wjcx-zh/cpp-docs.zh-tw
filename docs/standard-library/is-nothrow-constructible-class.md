---
title: "is_nothrow_constructible 類別 | Microsoft Docs"
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
  - "is_nothrow_constructible"
  - "std.is_nothrow_constructible"
  - "std::is_nothrow_constructible"
  - "type_traits/std::is_nothrow_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_constructible"
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_nothrow_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否為型別建構已知不會使用指定的引數型別時擲回。  
  
## 語法  
  
```  
template <class T, class... Args>  
    struct is_nothrow_constructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
 `Args`  
 要比對中的建構函式的引數型別 `T`。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 使用中的引數型別是開放式 `Args`, ，建構函式已知，編譯器不會擲回，否則保留 false。 型別 `T` 建構如果變數定義 `T t(std::declval<Args>()...);` 的格式正確。 同時 `T` 中的所有型別和 `Args` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)