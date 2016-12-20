---
title: "queue::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考成員 [STL/CLR]"
ms.assetid: cca05237-5b95-4cca-ac21-b786aa8a3c96
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的參考類型。  
  
## 語法  
  
```  
typedef value_type% reference;  
```  
  
## 備註  
 型別描述的項目參考。  
  
## 範例  
  
```  
// cliext_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify back of queue and redisplay   
    Myqueue::reference ref = c1.back();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **b x**   
## 需求  
 **標題:** \<cliext\/佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)   
 [queue::value\_type](../dotnet/queue-value-type-stl-clr.md)