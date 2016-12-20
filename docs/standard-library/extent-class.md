---
title: "extent 類別 | Microsoft Docs"
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
  - "std.tr1.extent"
  - "extent"
  - "std::tr1::extent"
  - "std.extent"
  - "std::extent"
  - "type_traits/std::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent 類別 [TR1]"
  - "extent"
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# extent 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得陣列維度。  
  
## 語法  
  
```  
template<class Ty, unsigned I = 0>  
    struct extent;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
 `I`  
 要查詢的陣列界限  
  
## 備註  
 如果 `Ty` 是至少有 `I` 個維度的陣列類型，則類型查詢會保留 `I` 所指定之維度中的項目數。  如果 `Ty` 不是陣列型別或其等級小於 `I`，或者如果 `I` 為零，而且 `Ty` 的類型是「`U` 的未知界限陣列」，則類型查詢會保留 0 值。  
  
## 範例  
  
```  
// std_tr1__type_traits__extent.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "extent 0 == "   
        << std::extent<int[5][10]>::value << std::endl;   
    std::cout << "extent 1 == "   
        << std::extent<int[5][10], 1>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **範圍 0 \=\= 5**  
**範圍 1 \=\= 10**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_all\_extents 類別](../standard-library/remove-all-extents-class.md)   
 [remove\_extent 類別](../standard-library/remove-extent-class.md)