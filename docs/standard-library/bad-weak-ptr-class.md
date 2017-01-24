---
title: "bad_weak_ptr 類別 | Microsoft Docs"
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
  - "memory/std::tr1::bad_weak_ptr"
  - "std::tr1::bad_weak_ptr"
  - "bad_weak_ptr"
  - "tr1::bad_weak_ptr"
  - "tr1.bad_weak_ptr"
  - "std.tr1.bad_weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_weak_ptr 類別"
  - "bad_weak_ptr 類別 [TR1]"
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bad_weak_ptr 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

報告錯誤 weak\_ptr 例外狀況。  
  
## 語法  
  
```  
class bad_weak_ptr  
    : public std::exception {  
public:  
    bad_weak_ptr();  
    const char *what() throw();  
    };  
```  
  
## 備註  
 這個類別描述接受 [weak\_ptr 類別](../standard-library/weak-ptr-class.md) 類型引數的 [shared\_ptr 類別](../standard-library/shared-ptr-class.md) 建構函式可能擲回的例外狀況。  成員函式 `what` 會傳回 `"bad_weak_ptr"`。  
  
## 範例  
  
```  
// std_tr1__memory__bad_weak_ptr.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::weak_ptr<int> wp;   
  
     {   
    std::shared_ptr<int> sp(new int);   
    wp = sp;   
     }   
  
    try   
        {   
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired   
        }   
    catch (const std::bad_weak_ptr&)   
        {   
        std::cout << "bad weak pointer" << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
  **不正確的弱式指標**   
## 需求  
 **標頭：** \<memory\>  
  
 **命名空間:** std  
  
## 請參閱  
 [weak\_ptr 類別](../standard-library/weak-ptr-class.md)