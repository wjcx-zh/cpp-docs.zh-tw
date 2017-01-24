---
title: "is_unsigned 類別 | Microsoft Docs"
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
  - "std::tr1::is_unsigned"
  - "is_unsigned"
  - "std.tr1.is_unsigned"
  - "std.is_unsigned"
  - "std::is_unsigned"
  - "type_traits/std::is_unsigned"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_unsigned 類別 [TR1]"
  - "is_unsigned"
ms.assetid: ba5bec3d-796b-4e54-8595-a3941ec6a8dc
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_unsigned 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試類型是否為不帶正負號的整數。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_unsigned;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果類型 `Ty` 是不帶正負號的整數類型或 `cv-qualified` 不帶正負號的整數類型，則述詞類型的執行個體保存 true，否則保存 false。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_unsigned.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_unsigned<trivial> == " << std::boolalpha   
        << std::is_unsigned<trivial>::value << std::endl;   
    std::cout << "is_unsigned<int> == " << std::boolalpha   
        << std::is_unsigned<int>::value << std::endl;   
    std::cout << "is_unsigned<unsigned int> == " << std::boolalpha   
        << std::is_unsigned<unsigned int>::value << std::endl;   
    std::cout << "is_unsigned<float> == " << std::boolalpha   
        << std::is_unsigned<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_unsigned\<trivial\> \=\= false**  
**is\_unsigned\<int\> \=\= false**  
**is\_unsigned\<unsigned int\> \=\= true**  
**is\_unsigned\<float\> \=\= false**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_signed 類別](../standard-library/is-signed-class.md)