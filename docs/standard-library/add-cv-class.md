---
title: "add_cv 類別 | Microsoft Docs"
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
  - "std.tr1.add_cv"
  - "add_cv"
  - "std::tr1::add_cv"
  - "std.add_cv"
  - "std::add_cv"
  - "type_traits/std::add_cv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_cv 類別 [TR1]"
  - "add_cv"
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_cv 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從類型建立 const\/volatile 類型。  
  
## 語法  
  
```  
template<class Ty>  
    struct add_cv;  
  
template<class T>  
using add_cv_t = typename add_cv<T>::type;  
```  
  
#### 參數  
 `Ty`  
 要修改的類型。  
  
## 備註  
 類型修飾詞的執行個體保留修改的類型 [add\_volatile 類別](../standard-library/add-volatile-class.md)`<` [add\_const 類別](../standard-library/add-const-class.md)`<Ty> >`。  
  
## 範例  
  
```  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_cv_t<int> *p = (const volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_cv<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_cv\_t\<int\> \=\= int**   
## 需求  
 **標頭：**\<type\_traits\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_const 類別](../standard-library/remove-const-class.md)   
 [remove\_volatile 類別](../standard-library/remove-volatile-class.md)