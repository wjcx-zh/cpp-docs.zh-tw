---
title: "is_member_pointer 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::is_member_pointer"
  - "is_member_pointer"
  - "std.tr1.is_member_pointer"
  - "std.is_member_pointer"
  - "std::is_member_pointer"
  - "type_traits/std::is_member_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_member_pointer 類別 [TR1]"
  - "is_member_pointer"
ms.assetid: da07ff4e-9ee0-4baa-ad93-1741f10913d1
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_member_pointer 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試，如果型別是指標給成員。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_member_pointer;  
```  
  
#### 參數  
 `Ty`  
 查詢的型別。  
  
## 備註  
 這個型別述詞的執行個體之型別，則 `Ty` 是指向成員函式或成員指標物件，或 `cv-qualified` 表單其中一個項目，否則會保留為 false。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_member_pointer.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct functional   
    {   
    int f();   
    };   
  
int main()   
    {   
    std::cout << "is_member_pointer<trivial *> == "   
        << std::boolalpha   
        << std::is_member_pointer<trivial *>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int trivial::*> == "   
        << std::boolalpha   
        << std::is_member_pointer<int trivial::*>::value   
        << std::endl;   
    std::cout << "is_member_pointer<int (functional::*)()> == "   
        << std::boolalpha   
        << std::is_member_pointer<int (functional::*)()>::value   
        << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_member\_pointertrivial\<\*\> \=\= false**  
**is\_member\_pointerint\<true trivial::\*\> \=\=**  
**true is\_member\_pointerint\<\(functional::\*\) \(\=\=\)\>**   
## 需求  
 **標題:** \<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_member\_function\_pointer 類別](../standard-library/is-member-function-pointer-class.md)   
 [is\_member\_object\_pointer 類別](../standard-library/is-member-object-pointer-class.md)   
 [is\_pointer 類別](../standard-library/is-pointer-class.md)