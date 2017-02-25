---
title: "is_polymorphic 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_polymorphic"
  - "is_polymorphic"
  - "std::tr1::is_polymorphic"
  - "std.is_polymorphic"
  - "std::is_polymorphic"
  - "type_traits/std::is_polymorphic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_polymorphic 類別 [TR1]"
  - "is_polymorphic"
ms.assetid: 4e1704db-d6f9-4154-a100-0ba02a373f20
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# is_polymorphic 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否有虛擬函式。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_polymorphic;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果類型 `Ty` 是一個宣告或繼承虛擬函式的類別，則 predicate 類型的執行個體為 true，否則為 false。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_polymorphic.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    virtual ~throws()   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_polymorphic<trivial> == " << std::boolalpha   
        << std::is_polymorphic<trivial>::value << std::endl;   
    std::cout << "is_polymorphic<throws> == " << std::boolalpha   
        << std::is_polymorphic<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_polymorphic\<trivial\> \=\= false**  
**is\_polymorphic\<throws\> \=\= true**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_abstract 類別](../standard-library/is-abstract-class.md)