---
title: "alignment_of 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.alignment_of"
  - "std::tr1::alignment_of"
  - "alignment_of"
  - "std.alignment_of"
  - "std::alignment_of"
  - "type_traits/std::alignment_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "alignment_of 類別 [TR1]"
  - "alignment_of"
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# alignment_of 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得指定類型的對齊方式。  此結構是針對 [alignof](../cpp/alignof-and-alignas-cpp.md) 實作。  若只需要查詢對齊值，請直接使用 `alignof`。  當您需要整數常數 \(例如進行標記分派時\)，請使用 alignment\_of。  
  
## 語法  
  
```  
template<class Ty>  
    struct alignment_of;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 類型查詢會保存類型 `Ty` 的對齊值。  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [aligned\_storage 類別](../standard-library/aligned-storage-class.md)