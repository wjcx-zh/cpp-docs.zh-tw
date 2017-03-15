---
title: "stack::top (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::top"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top 成員 [STL/CLR]"
ms.assetid: 5d8b7b69-336e-4d01-8b91-413a17aa2533
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::top (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取最後一個項目。  
  
## 語法  
  
```  
reference top();  
```  
  
## 備註  
 成員函式傳回參考給受控制序列的最後一個項目，此序列不能為空序列。  您會用它來存取，最後一個項目，當您知道它存在。  
  
## 範例  
  
```  
// cliext_stack_top.cpp   
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
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**top\(\) \= c**  
 **a b x**   
## 需求  
 **標頭：** \<cliext\/stack\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [stack::top\_item](../dotnet/stack-top-item-stl-clr.md)