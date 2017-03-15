---
title: "deque::value_type (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::value_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_type 成員 [STL/CLR]"
ms.assetid: c48528c2-966c-4396-be3c-3b9054689dde
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# deque::value_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的類型。  
  
## 語法  
  
```  
typedef Value value_type;  
```  
  
## 備註  
 這個型別是樣板參數 `Value`的同義字。  
  
## 範例  
  
```  
// cliext_deque_value_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::deque<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::deque<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::const\_reference](../dotnet/deque-const-reference-stl-clr.md)   
 [deque::reference](../dotnet/deque-reference-stl-clr.md)