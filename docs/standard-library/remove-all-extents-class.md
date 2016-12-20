---
title: "remove_all_extents 類別 | Microsoft Docs"
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
  - "std.tr1.remove_all_extents"
  - "std::tr1::remove_all_extents"
  - "remove_all_extents"
  - "std.remove_all_extents"
  - "std::remove_all_extents"
  - "type_traits/std::remove_all_extents"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_all_extents 類別 [TR1]"
  - "remove_all_extents"
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
caps.latest.revision: 16
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove_all_extents 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從陣列類型建立非陣列類型。  
  
## 語法  
  
```  
template<class T>  
    struct remove_all_extents;  
  
template<class T>  
  using remove_all_extents_t = typename remove_all_extents<T>::type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 `remove_all_extents<T>` 執行個體儲存修改的類型，這是已移除所有陣列維度之陣列類型 `T` 的項目類型，如果 `T` 不是陣列類型則為 `T`。  
  
## 範例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "remove_all_extents<int> == "   
        << typeid(std::remove_all_extents_t<int>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5]> == "   
        << typeid(std::remove_all_extents_t<int[5]>).name()   
        << std::endl;   
    std::cout << "remove_all_extents_t<int[5][10]> == "   
        << typeid(std::remove_all_extents_t<int[5][10]>).name()   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_extent 類別](../standard-library/remove-extent-class.md)