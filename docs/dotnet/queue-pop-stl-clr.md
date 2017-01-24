---
title: "queue::pop (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::pop"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop 成員 [STL/CLR]"
ms.assetid: 38f6c03b-e8f8-4663-b3d6-18314cdc8e7d
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::pop (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除最後一個項目。  
  
## 語法  
  
```  
void pop();  
```  
  
## 備註  
 成員函式移除受控制序列的最後一個項目，此序列不能為空序列。  您可以使用它從佇列的尾端縮短一個項目。  
  
## 範例  
  
```  
// cliext_queue_pop.cpp   
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
  
  **a b c**  
 **b c**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::push](../dotnet/queue-push-stl-clr.md)