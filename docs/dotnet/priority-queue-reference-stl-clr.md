---
title: "priority_queue::reference (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "參考成員 [STL/CLR]"
ms.assetid: b063eaf1-c238-4aef-ac54-a81d0f671418
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::reference (STL/CLR)
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
// cliext_priority_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c a b**  
 **x a b**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)