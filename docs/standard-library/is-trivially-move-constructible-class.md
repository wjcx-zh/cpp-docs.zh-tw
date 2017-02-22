---
title: "is_trivially_move_constructible 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_move_constructible"
  - "std.is_trivially_move_constructible"
  - "std::is_trivially_move_constructible"
  - "type_traits/std::is_trivially_move_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_move_constructible"
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# is_trivially_move_constructible 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有 trivial 移動建構函式。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_trivially_move_constructible;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 類型是具有 trivial 移動建構函式的類別，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
 在下列情況下，類別 `Ty` 的移動建構函式是 trivial：  
  
 它是隱含宣告  
  
 其參數類型相等於隱含宣告的參數類型  
  
 類別 `Ty` 沒有虛擬函式  
  
 類別 `Ty` 沒有虛擬基底  
  
 類別沒有任何變動性的非靜態資料成員  
  
 類別 `Ty` 的所有直接基底都有 trivial 移動建構函式  
  
 類別類型的所有非靜態資料成員的類別都具有 trivial 移動建構函式  
  
 類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 移動建構函式  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)