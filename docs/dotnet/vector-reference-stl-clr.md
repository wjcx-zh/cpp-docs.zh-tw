---
title: "vector::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考成員 [STL/CLR]"
ms.assetid: 6ea0d3b0-d2e6-42c3-856c-a10f5ef7620c
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的參考類型。  
  
## 語法  
  
```  
typedef value_type% reference;  
```  
  
## 備註  
 類型描述項目的參考。  
  
## 範例  
  
```  
// cliext_vector_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **A B C**   
## 需求  
 **標頭：** \<cliext\/vector\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::const\_reference](../dotnet/vector-const-reference-stl-clr.md)   
 [vector::value\_type](../dotnet/vector-value-type-stl-clr.md)