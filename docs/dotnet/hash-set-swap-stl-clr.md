---
title: "hash_set::swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 成員 [STL/CLR]"
ms.assetid: 6476e48f-4744-486d-b028-cf0a048acd4d
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交換兩個容器的內容。  
  
## 語法  
  
```  
void swap(hash_set<Key>% right);  
```  
  
#### 參數  
 right  
 要交換內容的容器。  
  
## 備註  
 成員函式交換在 `this` 和 `right`的控制順序。  它在常數時間執行，而且不會擲回例外狀況。  您將它當做一個快速的方法交換兩個容器的內容。  
  
## 範例  
  
```  
// cliext_hash_set_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_set c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **d e f**  
 **d e f**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::operator\=](../dotnet/hash-set-operator-assign-stl-clr.md)