---
title: "hash_set::generic_reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::generic_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_reverse_iterator 成員 [STL/CLR]"
ms.assetid: ffec7e08-07e4-49cf-b2f2-679c6a2a450c
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::generic_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反向 Iterator 的型別為具有泛型介面的容器使用的。  
  
## 語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
## 備註  
 型別描述可以與泛型介面為這個樣板容器類別的泛型反向 Iterator。  
  
## 範例  
  
```  
// cliext_hash_set_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_set::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_set::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_set::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **c**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::generic\_container](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash\_set::generic\_iterator](../dotnet/hash-set-generic-iterator-stl-clr.md)