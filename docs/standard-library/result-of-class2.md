---
title: "result_of 類別 | Microsoft Docs"
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
  - "functional/std::tr1::result_of"
  - "std::tr1::result_of"
  - "result_of"
  - "std.tr1.result_of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "result_of 類別 [TR1]"
ms.assetid: 14ec0040-07f1-45a5-80b5-d0c9f9b00c8f
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# result_of 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝的可呼叫物件的傳回型別。  
  
## 語法  
  
```  
template<class Ty>  
    struct result_of {  
    typedef T0 type;  
    };  
```  
  
#### 參數  
 `Ty`  
 函式呼叫的描述 \(請參閱 \< 備註 \> 一節\)。  
  
## 備註  
 樣板類別會定義成員的 `type` ，其樣板引數描述的函式呼叫之傳回型別的同義字則為 `Ty`。  樣板引數必須是表單 `Fty(T1, T2, ..., TN)`， `Fty` 是一個可呼叫的型別。  範本是以套用的第一個以下規則決定傳回型別:  
  
-   如果 `Fty` 是函式的指標型別 `R(*)(U1, U2, ..., UN)` 傳回型別為 `R`;  
  
-   如果 `Fty` 是函式型別 `R(&)(U1, U2, ..., UN)` 的參考傳回型別為 `R`;  
  
-   如果 `Fty` 是指向成員函式型別 `R(U1::*)(U2, ..., UN)` 傳回型別為 `R`;  
  
-   如果 `Fty` 是指向資料成員型別 `R U1::*` 傳回型別為 `R`;  
  
-   如果 `Fty` 是與成員 typedef `result_type` 的類別傳回型別為 `Fty::result_type`;  
  
-   如果 `N` 為 0 \(即 `Ty` 的格式為 `Fty()`\) 傳回型別為 `void`;  
  
-   如果 `Fty` 是與成員樣板的類別命名為傳回型別為 `Fty::result<T1, T2, ..., TN>::type`的 `result` ;  
  
-   在其他所有情況下它是錯誤。  
  
## 範例  
  
```  
// std_tr1__functional__result_of.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
double square(double x)   
    {   
    return (x * x);   
    }   
  
template<class Fun,   
    class Arg>   
    void test_result(const Fun& fun, Arg arg)   
    {   
    typename std::result_of<Fun(Arg)>::type val = fun(arg);   
    std::cout << "val == " << val << std::endl;   
    }   
  
int main()   
    {   
    test_result(&square, 3.0);   
  
    return (0);   
    }  
  
```  
  
  **val \=\= 9**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std