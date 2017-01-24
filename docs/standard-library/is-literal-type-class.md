---
title: "is_literal_type 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_literal_type"
  - "std.is_literal_type"
  - "std::is_literal_type"
  - "type_traits/std::is_literal_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_literal_type"
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_literal_type 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試是否為型別可用來當做 `constexpr` 變數或建構、 使用或傳回 `constexpr` 函式。  
  
## 語法  
  
```  
template <class T>  
    struct is_literal_type;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果為 true，則保留 predicate 類型的執行個體型別 `T` 是 *常值型別*, ，否則保留 false。 常值的型別是 `void`, ，純量型別、 參考型別、 型別的陣列常值或常值的類別型別。 常值的類別型別是有 trivial 解構函式的類別類型、 為彙總類型或具有至少一個非移動，非複製 `constexpr` 建構函式，以及所有它的基底類別和非靜態資料成員是靜態的常值型別。 常值類型的概念雖然常值的型別一定是常值的型別，包括任何項目，編譯器可以評估為 `constexpr` 在編譯時期。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)