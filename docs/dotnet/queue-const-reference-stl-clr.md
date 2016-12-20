---
title: "queue::const_reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::const_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reference 成員 [STL/CLR]"
ms.assetid: e2398b75-e072-4769-82df-f2607e29c6e4
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::const_reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的常數參考類型。  
  
## 語法  
  
```  
typedef value_type% const_reference;  
```  
  
## 備註  
 型別描述之項目的常數參考。  
  
## 範例  
  
```  
// cliext_queue_const_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Myqueue::const_reference cref = c1.front();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標題:** \<cliext\/佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::reference](../dotnet/queue-reference-stl-clr.md)   
 [queue::value\_type](../dotnet/queue-value-type-stl-clr.md)