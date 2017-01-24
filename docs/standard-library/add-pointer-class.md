---
title: "add_pointer 類別 | Microsoft Docs"
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
  - "std::tr1::add_pointer"
  - "std.tr1.add_pointer"
  - "add_pointer"
  - "std.add_pointer"
  - "std::add_pointer"
  - "type_traits/std::add_pointer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_pointer 類別 [TR1]"
  - "add_pointer"
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_pointer 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從指定的類型建立類型指標。  
  
## 語法  
  
```  
template<class Ty>  
    struct add_pointer;  
  
template<class T>  
using add_pointer_t = typename add_pointer<T>::type;  
```  
  
#### 參數  
 `Ty`  
 要修改的類型。  
  
## 備註  
 成員 typedef 類型名稱和 `remove_reference<T>::type*` 類型相同。  
  
 由於不能從參考建立指標，因此在建立類型指標之前，`add_pointer` 會從指定的類型移除參考 \(如果有的話\)。  因此，您可以使用類型與 `add_pointer`，而不用擔心類型是否為參考。  
  
## 範例  
 下列範例會示範，類型的 `add_pointer` 與該類型的指標相同。  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_pointer_t<int> *p = (int **)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_pointer_t<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_pointer\_t\<int\> \=\= int \***   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_pointer 類別](../standard-library/remove-pointer-class.md)