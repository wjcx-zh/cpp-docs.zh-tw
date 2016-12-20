---
title: "multimap::end (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end 成員 [STL/CLR]"
ms.assetid: 8d3f9347-794d-4bd3-9bd1-50534fcf4ffe
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控制序列的結尾。  
  
## 語法  
  
```  
iterator end();  
```  
  
## 備註  
 成員函式傳回一個雙向迭代器，其指向受控制序列的尾端。  您可用它來取得指向受控制序列結尾的迭代器；即使受控制序列的長度變更，它的狀態也不會變更。  
  
## 範例  
  
```  
// cliext_multimap_end.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymultimap::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**\*\-\- \-\-end\(\) \= \[b 2\]**  
**\*\-\-end\(\) \= \[c 3\]**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::begin](../dotnet/multimap-begin-stl-clr.md)