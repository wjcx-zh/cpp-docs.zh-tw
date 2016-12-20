---
title: "is_compound 類別 | Microsoft Docs"
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
  - "std::tr1::is_compound"
  - "is_compound"
  - "std.tr1.is_compound"
  - "std.is_compound"
  - "std::is_compound"
  - "type_traits/std::is_compound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_compound 類別 [TR1]"
  - "is_compound"
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
caps.latest.revision: 21
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_compound 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試指定的類型是否不是基本。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_compound;  
```  
  
#### 參數  
 `Ty`  
 要查詢的類型。  
  
## 備註  
 如果 `Ty` 的類型是一個基本類型，類型述詞的執行個體會保存 `false` \(亦即，如果 [is\_fundamental](../standard-library/is-fundamental-class.md)`<``Ty``>` 會保存 `true`\)；否則它會保存 `true`。  因此，如果 `Ty` 是陣列類型、函式類型或 `void` 的指標或物件或函式、參考、類別、聯集、列舉或非靜態類別成員的指標，或其中一個 *cv\-qualified* 形式，述詞會保存 `true`。  
  
## 範例  
  
```  
// std_tr1__type_traits__is_compound.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_compound<trivial> == " << std::boolalpha   
        << std::is_compound<trivial>::value << std::endl;   
    std::cout << "is_compound<int[]> == " << std::boolalpha   
        << std::is_compound<int[]>::value << std::endl;   
    std::cout << "is_compound<int()> == " << std::boolalpha   
        << std::is_compound<int()>::value << std::endl;   
    std::cout << "is_compound<int&> == " << std::boolalpha   
        << std::is_compound<int&>::value << std::endl;   
    std::cout << "is_compound<void *> == " << std::boolalpha   
        << std::is_compound<void *>::value << std::endl;   
    std::cout << "is_compound<int> == " << std::boolalpha   
        << std::is_compound<int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_compound\<trivial\> \=\= true**  
**is\_compound\<int\[\]\> \=\= true**  
**is\_compound\<int\(\)\> \=\= true**  
**is\_compound\<int&\> \=\= true**  
**is\_compound\<void \*\> \=\= true**  
**is\_compound\<int\> \=\= false**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [is\_class 類別](../standard-library/is-class-class.md)