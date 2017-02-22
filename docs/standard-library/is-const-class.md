---
title: "is_const 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.is_const"
  - "is_const"
  - "std::tr1::is_const"
  - "std.is_const"
  - "std::is_const"
  - "type_traits/std::is_const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_const 類別 [TR1]"
  - "is_const"
ms.assetid: 55b8e887-9c3f-4a1d-823a-4a257337b205
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# is_const 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為 const。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_const;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 是 `const-qualified`，類型述詞的執行個體會保留 true。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_const<trivial> == " << std::boolalpha   
        << std::is_const<trivial>::value << std::endl;   
    std::cout << "is_const<const trivial> == " << std::boolalpha   
        << std::is_const<const trivial>::value << std::endl;   
    std::cout << "is_const<int> == " << std::boolalpha   
        << std::is_const<int>::value << std::endl;   
    std::cout << "is_const<const int> == " << std::boolalpha   
        << std::is_const<const int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_const\<trivial\> \=\= false**  
**is\_const\<const trivial\> \=\= true**  
**is\_const\<int\> \=\= false**  
**is\_const\<const int\> \=\= true**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_volatile 類別](../standard-library/is-volatile-class.md)