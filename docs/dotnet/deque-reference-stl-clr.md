---
title: "deque::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考成員 [STL/CLR]"
ms.assetid: 059f023b-f60c-451b-8944-162cc14ca862
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::reference (STL/CLR)
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
// cliext_deque_reference.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::deque<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::deque<wchar_t>::reference ref = *it;   
  
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
 **標頭：** \<cliext\/deque\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::const\_reference](../dotnet/deque-const-reference-stl-clr.md)   
 [deque::value\_type](../dotnet/deque-value-type-stl-clr.md)