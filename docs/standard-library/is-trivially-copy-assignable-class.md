---
title: "is_trivially_copy_assignable | Microsoft Docs"
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
  - "is_trivially_copy_assignable"
  - "std.is_trivially_copy_assignable"
  - "std::is_trivially_copy_assignable"
  - "type_traits/std::is_trivially_copy_assignable"
dev_langs: 
  - "C++"
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
caps.latest.revision: 12
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_copy_assignable
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有 trivial 複製指派運算子。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_trivially_copy_constructible;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 類型是具有 trivial 複製指派運算子的類別，則 predicate 類型的執行個體保留 true，否則保留 false。  
  
 在下列情況下，類別 `Ty` 的指派建構函式是 trivial：  
  
 它會隱含地提供  
  
 類別 `Ty` 沒有虛擬函式  
  
 類別 `Ty` 沒有虛擬基底  
  
 類別類型的所有非靜態資料成員的類別具有 trivial 指派運算子  
  
 類別的類型陣列的所有非靜態資料成員的類別具有 trivial 指派運算子  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)