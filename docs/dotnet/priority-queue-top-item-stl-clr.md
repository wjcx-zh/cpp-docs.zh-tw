---
title: "priority_queue::top_item (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::top_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top_item 成員 [STL/CLR]"
ms.assetid: d497403b-6b1d-4c6e-a0f4-c744cc5fad75
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# priority_queue::top_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取最高優先權的項目。  
  
## 語法  
  
```  
property value_type back_item;  
```  
  
## 備註  
 屬性存取受控制序列的頂端 \(最高優先權的\) 項目，必須為非空白。  用來讀取或寫入最高優先權的項目，也就是說，當您知道它時。  
  
## 範例  
  
```  
// cliext_priority_queue_top_item.cpp   
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
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b**  
**top\_item \= c**  
 **x b**   
## 需求  
 **標題:** \<cliext\/佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::top](../dotnet/priority-queue-top-stl-clr.md)