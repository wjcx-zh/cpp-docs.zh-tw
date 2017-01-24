---
title: "is_trivial 類別 | Microsoft Docs"
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
  - "is_trivial"
  - "std.is_trivial"
  - "std::is_trivial"
  - "type_traits/std::is_trivial"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivial"
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivial 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為 trivial 類型。  
  
## 語法  
  
```  
template <class T>  
    struct is_trivial;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果類型 `T` 是 trivial 類型，則類型述詞的執行個體為 true，否則為 false。 trivial 類型是純量類型、可完整複製類別類型、這些類型的陣列和 cv 限定版本。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)