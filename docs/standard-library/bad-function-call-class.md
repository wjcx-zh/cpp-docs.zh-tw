---
title: "bad_function_call 類別 | Microsoft Docs"
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
  - "std::tr1::bad_function_call"
  - "functional/std::tr1::bad_function_call"
  - "std.tr1.bad_function_call"
  - "bad_function_call"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_function_call 類別 [TR1]"
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bad_function_call 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

報告錯誤的函式呼叫。  
  
## 語法  
  
```  
class bad_function_call  
    : public std::exception {  
    };  
```  
  
## 備註  
 因為物件是空的，描述例外狀況的類別表示呼叫到失敗的函式物件的 `operator()` 。  
  
## 範例  
  
```  
// std_tr1__functional__bad_function_call.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
typedef double (Fd)(double);   
typedef std::function<Fd> Myfunc;   
  
double square(double x)   
    {   
    return (x * x);   
    }   
  
int main()   
    {   
    Myfunc fd0(square);   
    std::cout << "x * x == " << fd0(3) << std::endl;   
  
    try   
        {   
        Myfunc fd1;   
        std::cout << fd1(3) << std::endl;   
        }   
    catch (const std::bad_function_call&)   
        {   
        std::cout << "bad function call" << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
  **x \* x \=\= 9**  
**解構函式呼叫**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std