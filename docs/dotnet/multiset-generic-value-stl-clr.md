---
title: "multiset::generic_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::generic_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_value 成員 [STL/CLR]"
ms.assetid: 4b77b5f8-1e69-48b3-b523-c92ab538a29f
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::generic_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的型別為具有泛型介面的容器使用的。  
  
## 語法  
  
```  
typedef GValue generic_value;  
```  
  
## 備註  
 型別描述儲存的項目值為與泛型介面來使用這個樣板容器類別的型別 `GValue` 的物件。  
  
## 範例  
  
```  
// cliext_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultiset::generic_iterator gcit = gc1->begin();   
    Mymultiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::generic\_container](../dotnet/multiset-generic-container-stl-clr.md)   
 [multiset::generic\_iterator](../dotnet/multiset-generic-iterator-stl-clr.md)   
 [multiset::generic\_reverse\_iterator](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)