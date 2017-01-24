---
title: "remove_const 類別 | Microsoft Docs"
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
  - "std.tr1.remove_const"
  - "std::tr1::remove_const"
  - "remove_const"
  - "std.remove_const"
  - "std::remove_const"
  - "type_traits/std::remove_const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_const 類別 [TR1]"
  - "remove_const"
ms.assetid: feb76fb3-9228-41d6-80f6-2fbb04daec43
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remove_const 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從類型建立非常數類型。  
  
## 語法  
  
```  
template<class T>  
    struct remove_const;  
```  
  
```  
template<class T>  
  using remove_const_t = typename remove_const<T>::type;  
```  
  
#### 參數  
 `T`  
 要修改的類型。  
  
## 備註  
 `remove_const<T>` 執行個體儲存修改的類型，如果 `T1` 的格式為 `T`，類型為 `const T1`，否則為 `T`。  
  
## 範例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_const_t<const int>*)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_const_t<const int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **remove\_const\_t\<const int\> \=\= int**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_const 類別](../standard-library/add-const-class.md)   
 [remove\_cv 類別](../standard-library/remove-cv-class.md)