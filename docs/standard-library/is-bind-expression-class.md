---
title: "is_bind_expression 類別 | Microsoft Docs"
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
  - "std.tr1.is_bind_expression"
  - "is_bind_expression"
  - "std::tr1::is_bind_expression"
  - "functional/std::tr1::is_bind_expression"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_bind_expression 類別 [TR1]"
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_bind_expression 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試，如果呼叫所產生的 `bind`型別。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_bind_expression {  
    static const bool value;  
    };  
```  
  
## 備註  
 常數值 `value` 為 true，如果型別是 `Ty` 呼叫所傳回的型別設定為 `bind`，否則為 false。  
  
## 範例  
  
```  
// std_tr1__functional__is_bind_expression.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
void square(double x)   
    {   
    std::cout << x << "^2 == " << x * x << std::endl;   
    }   
  
template<class Expr>   
    void test_for_bind(const Expr&)   
    {   
    std::cout << std::is_bind_expression<Expr>::value << std::endl;   
    }   
  
int main()   
    {   
    test_for_bind(3.0 * 3.0);   
    test_for_bind(std::bind(square, 3));   
  
    return (0);   
    }  
  
```  
  
  **0**  
**1**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [bind 函式](../Topic/bind%20Function.md)