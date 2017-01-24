---
title: "is_void 類別 | Microsoft Docs"
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
  - "is_void"
  - "std.tr1.is_void"
  - "std::tr1::is_void"
  - "std.is_void"
  - "std::is_void"
  - "type_traits/std::is_void"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_void 類別 [TR1]"
  - "is_void"
ms.assetid: 99b0de3b-1b38-4949-b053-080e5363174e
caps.latest.revision: 21
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_void 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為 void。  
  
## 語法  
  
```  
template<class T>  
    struct is_void;  
```  
  
#### 參數  
 `T`  
 要查詢的類型。  
  
## 備註  
 如果類型 `T` 是 `void` 或 `void` 的 cv 限定表單，則類型述詞的執行個體為 true，否則為 false。  
  
## 範例  
  
```cpp  
// std__type_traits__is_void.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_void<trivial> == " << std::boolalpha   
        << std::is_void<trivial>::value << std::endl;   
    std::cout << "is_void<void()> == " << std::boolalpha   
        << std::is_void<void()>::value << std::endl;   
    std::cout << "is_void<void> == " << std::boolalpha   
        << std::is_void<void>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_void<trivial> == false is_void<void()> == false is_void<void> == true  
```  
  
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)