---
title: "deque::generic_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::generic_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_iterator 成員 [STL/CLR]"
ms.assetid: 865d1ec3-e660-4d18-9ff7-2302a3e74d49
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::generic_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

迭代器的型別，適合與容器的泛型介面一起使用。  
  
## 語法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value> generic_iterator;  
```  
  
## 備註  
 描述泛型迭代器的型別，其適合與此樣本容器類別的泛型介面一起使用。  
  
## 範例  
  
```  
// cliext_deque_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::deque<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::deque<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::deque<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a a c**   
## 需求  
 **標頭：** \<cliext\/deque\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)   
 [deque::generic\_reverse\_iterator](../dotnet/deque-generic-reverse-iterator-stl-clr.md)