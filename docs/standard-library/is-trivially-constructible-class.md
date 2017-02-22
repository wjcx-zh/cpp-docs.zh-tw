---
title: "is_trivially_constructible 類別 | Microsoft Docs"
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
  - "is_trivially_constructible"
  - "std.is_trivially_constructible"
  - "std::is_trivially_constructible"
  - "type_traits/std::is_trivially_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_constructible"
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_trivially_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否巨細靡遺地建構，會使用指定的引數型別時。  
  
## 語法  
  
```  
template <class T, class... Args>  
    struct is_trivially_constructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
 `Args`  
 要比對中的建構函式的引數型別 `T`。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 使用中的引數型別是巨細靡遺地建構 `Args`, ，否則保留 false。 型別 `T` 巨細靡遺地建構如果變數定義 `T t(std::declval<Args>()...);` 格式正確，並且知道呼叫任何非一般的作業。 同時 `T` 中的所有型別和 `Args` 必須是完整的型別， `void`, ，或無法辨識的繫結的陣列。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)