---
title: "is_pointer 類別 | Microsoft Docs"
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
  - "std.tr1.is_pointer"
  - "is_pointer"
  - "std::tr1::is_pointer"
  - "std.is_pointer"
  - "std::is_pointer"
  - "type_traits/std::is_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_pointer 類別 [TR1]"
  - "is_pointer"
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_pointer 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為指標。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_pointer;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果類型 `Ty` 是 `void` 的指標、物件的指標、函式的指標，或形成其中之一的 `cv-qualified` 的指標，則類型述詞的執行個體為 true，否則為 false。  請注意，如果 `Ty` 是成員的指標或成員函式的指標，則 `is_pointer` 會保留 false。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pointer<trivial> == " << std::boolalpha   
        << std::is_pointer<trivial>::value << std::endl;   
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha   
        << std::is_pointer<int trivial::*>::value << std::endl;   
    std::cout << "is_pointer<trivial *> == " << std::boolalpha   
        << std::is_pointer<trivial *>::value << std::endl;   
    std::cout << "is_pointer<int> == " << std::boolalpha   
        << std::is_pointer<int>::value << std::endl;   
    std::cout << "is_pointer<int *> == " << std::boolalpha   
        << std::is_pointer<int *>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_pointer\<trivial\> \=\= false**  
**is\_pointer\<int trivial::\*\> \=\= false**  
**is\_pointer\<trivial \*\> \=\= true**  
**is\_pointer\<int\> \=\= false**  
**is\_pointer\<int \*\> \=\= true**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_member\_pointer 類別](../standard-library/is-member-pointer-class.md)   
 [is\_reference 類別](../standard-library/is-reference-class.md)