---
title: "list::reverse (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::reverse"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse 成員 [STL/CLR]"
ms.assetid: de3bce1e-01fe-461d-a785-5cf4fcea988f
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::reverse (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

反轉受控制序列。  
  
## 語法  
  
```  
void reverse();  
```  
  
## 備註  
 成員函式反轉所有項目順序在受控制序列的。  您會用它來反映項目清單。  
  
## 範例  
  
```  
// cliext_list_reverse.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **c b。**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)