---
title: "priority_queue::pop (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::pop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop 成員 [STL/CLR]"
ms.assetid: d363b3f1-247b-466a-a300-c5918b0dfd4e
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::pop (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除最高 proirity 的項目。  
  
## 語法  
  
```  
void pop();  
```  
  
## 備註  
 成員函式中受控制序列的最高優先權的項目，此序列必須為非空白。  您可以使用它由項目縮短佇列在後面。  
  
## 範例  
  
```  
// cliext_priority_queue_pop.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b**  
 **b。**   
## 需求  
 **標題:** \<cliext\/佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::push](../dotnet/priority-queue-push-stl-clr.md)