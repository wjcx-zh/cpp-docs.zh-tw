---
title: "is_trivially_copy_constructible 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_copy_constructible"
  - "std.is_trivially_copy_constructible"
  - "std::is_trivially_copy_constructible"
  - "type_traits/std::is_trivially_copy_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_copy_constructible"
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# is_trivially_copy_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否 trivial 複製建構函式。  
  
## 語法  
  
```  
template<class T>  
    struct is_trivially_copy_constructible;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果 `T` 類型是具有 trivial 複製建構函式的類別，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
 類別的複製建構函式 `T` 是如果它以隱含方式宣告，此類別的一般 `T` 沒有虛擬函式或虛擬基底類別的所有直接基底 `T` 有 trivial 複製建構函式、 類別類型的所有非靜態資料成員的類別有 trivial 複製建構函式和類別的類型陣列的所有非靜態資料成員的類別有 trivial 複製建構函式。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)