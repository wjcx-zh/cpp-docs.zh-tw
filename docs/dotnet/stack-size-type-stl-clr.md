---
title: "stack::size_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::size_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_type 成員 [STL/CLR]"
ms.assetid: 713ba8c5-41e5-422a-a334-cfeab16b4496
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::size_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

兩個項目之間的帶正負號距離的類型。  
  
## 語法  
  
```  
typedef int size_type;  
```  
  
## 備註  
 描述非負數項目計數的型別。  
  
## 範例  
  
```  
// cliext_stack_size_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Mystack::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size difference \= 2**   
## 需求  
 **標頭：** \<cliext\/stack\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [stack::empty](../dotnet/stack-empty-stl-clr.md)