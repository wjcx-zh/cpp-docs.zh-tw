---
title: "_1 物件 | Microsoft Docs"
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
  - "std.tr1._1"
  - "_1"
  - "std::tr1::_1"
  - "functional/std::tr1::_1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_1 物件 [TR1]"
ms.assetid: 30c3c480-ff31-4708-94be-7d0d65f243c9
caps.latest.revision: 24
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _1 物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可取代引數的預留位置。  
  
## 語法  
  
```  
namespace placeholders {  
  extern unspecified _1, _2, ... _M  
  } // namespace placeholders (within std)  
```  
  
## 備註  
 `_1, _2, ... _M` 物件是在對 [bind 函式](../Topic/bind%20Function.md) 所傳回之物件的函式呼叫中分別指定第一個、第二個、…、第 M 個引數的預留位置。  您可以使用 `_N` 指定當繫結評估運算式時，要插入第 N 個引數的位置。  
  
 在此實作中，`M` 的值是 20。  
  
## 範例  
  
```cpp  
// std__functional_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)   
    {   
    std::cout << x << "^2 == " << x * x << std::endl;   
    }   
  
void product(double x, double y)   
    {   
    std::cout << x << "*" << y << " == " << x * y << std::endl;   
    }   
  
int main()   
    {   
    double arg[] = {1, 2, 3};   
  
    std::for_each(&arg[0], &arg[3], square);   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(product, _1, 2));   
    std::cout << std::endl;   
  
    std::for_each(&arg[0], &arg[3], std::bind(square, _1));   
  
    return (0);   
    }  
  
```  
  
  **1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**  
**1\*2 \=\= 2**  
**2\*2 \=\= 4**  
**3\*2 \=\= 6**  
**1^2 \=\= 1**  
**2^2 \=\= 4**  
**3^2 \=\= 9**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [bind 函式](../Topic/bind%20Function.md)   
 [is\_placeholder 類別](../standard-library/is-placeholder-class.md)