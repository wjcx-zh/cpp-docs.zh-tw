---
title: "queue::generic_value (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::queue::generic_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_value 成員 [STL/CLR]"
ms.assetid: 5efd9812-6b4d-4e59-b8e8-c4975ae61667
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# queue::generic_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

項目的型別為具有泛型介面的容器使用的。  
  
## 語法  
  
```  
typedef GValue generic_value;  
```  
  
## 備註  
 型別描述儲存的項目值為與泛型介面來使用這個樣板容器類別的型別 `GValue` 的物件。\(`GValue` 是 `value_type` 或 `value_type^` ，如果 `value_type` 為參考型別\)。  
  
## 範例  
  
```  
// cliext_queue_generic_value.cpp   
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
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::value\_type](../dotnet/queue-value-type-stl-clr.md)