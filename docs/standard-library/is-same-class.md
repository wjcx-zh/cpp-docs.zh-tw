---
title: "is_same 類別 | Microsoft Docs"
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
  - "std::tr1::is_same"
  - "std.tr1.is_same"
  - "is_same"
  - "std.is_same"
  - "std::is_same"
  - "type_traits/std::is_same"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_same 類別 [TR1]"
  - "is_same"
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_same 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試兩個類型是否相同。  
  
## 語法  
  
```  
template<class Ty1, class Ty2>  
    struct is_same;  
```  
  
#### 參數  
 `Ty1`  
 要查詢的第一個類型。  
  
 `Ty2`  
 要查詢的第二個類型。  
  
## 備註  
 如果類型 `Ty1` 與 `Ty2` 相同，則類型述詞的執行個體為 true，否則為 false。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_same.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct base   
    {   
    int val;   
    };   
  
struct derived   
    : public base   
    {   
    };   
  
int main()   
    {   
    std::cout << "is_same<base, base> == " << std::boolalpha   
        << std::is_same<base, base>::value << std::endl;   
    std::cout << "is_same<base, derived> == " << std::boolalpha   
        << std::is_same<base, derived>::value << std::endl;   
    std::cout << "is_same<derived, base> == " << std::boolalpha   
        << std::is_same<derived, base>::value << std::endl;   
    std::cout << "is_same<int, int> == " << std::boolalpha   
        << std::is_same<int, int>::value << std::endl;   
    std::cout << "is_same<int, const int> == " << std::boolalpha   
        << std::is_same<int, const int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_same\<base, base\> \=\= true**  
**is\_same\<base, derived\> \=\= false**  
**is\_same\<derived, base\> \=\= false**  
**is\_same\<int, int\> \=\= true**  
**is\_same\<int, const int\> \=\= false**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_convertible 類別](../standard-library/is-convertible-class.md)   
 [is\_base\_of 類別](../standard-library/is-base-of-class.md)