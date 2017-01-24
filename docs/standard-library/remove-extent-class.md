---
title: "remove_extent 類別 | Microsoft Docs"
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
  - "std::tr1::remove_extent"
  - "std.tr1.remove_extent"
  - "remove_extent"
  - "std.remove_extent"
  - "std::remove_extent"
  - "type_traits/std::remove_extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_extent 類別 [TR1]"
  - "remove_extent"
ms.assetid: b9320862-3891-49fc-80bc-571eb2c035cf
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove_extent 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從陣列類型建立項目類型。  
  
## 語法  
  
```  
template<class T>  
    struct remove_extent;  
  
template<class T>  
using remove_extent_t = typename remove_extent<T>::type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 `remove_extent<T>` 執行個體儲存修改的類型，如果 `T1` 的格式為 `T`，類型為 `T1[N]`，否則為 `T`。  
  
## 範例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "remove_extent_t<int> == "  
        << typeid(std::remove_extent_t<int>).name()  
        << std::endl;T  
    std::cout << "remove_extent_t<int[5]> == "  
        << typeid(std::remove_extent_t<int[5]>).name()  
        << std::endl;T  
    std::cout << "remove_extent_t<int[5][10]> == "  
        << typeid(std::remove_extent_t<int[5][10]>).name()  
        << std::endl;   
    return (0);   
    }  
  
```  
  
  **remove\_extent\_t\<int\> \=\= int**  
**remove\_extent\_t\<int\[5\]\> \=\= int**  
**remove\_extent\_t\<int\[5\]\[10\]\> \=\= int \[10\]**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_all\_extents 類別](../standard-library/remove-all-extents-class.md)