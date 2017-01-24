---
title: "is_placeholder 類別 | Microsoft Docs"
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
  - "is_placeholder"
  - "std.tr1.is_placeholder"
  - "functional/std::tr1::is_placeholder"
  - "std::tr1::is_placeholder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_placeholder 類別 [TR1]"
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_placeholder 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試，如果型別是替代符號。  
  
## 語法  
  
```  
template<class Ty>  
    struct is_placeholder {  
    static const int value;  
    };  
```  
  
## 備註  
 如果 `Ty` 型別不是替代符號，常數值 `value` 為 0;否則，它的值是函式呼叫的引數它繫結。  您會用它來判斷第 n 預留位置的 `_N`值為 `N` 。  
  
## 範例  
  
```  
// std_tr1__functional__is_placeholder.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
using namespace std::placeholders;   
  
template<class Expr>   
    void test_for_placeholder(const Expr&)   
    {   
    std::cout << std::is_placeholder<Expr>::value << std::endl;   
    }   
  
int main()   
    {   
    test_for_placeholder(3.0);   
    test_for_placeholder(_3);   
  
    return (0);   
    }  
  
```  
  
  **0**  
**3**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\_1 物件](../standard-library/1-object.md)