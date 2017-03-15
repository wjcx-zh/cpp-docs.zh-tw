---
title: "multimap::size (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size 成員 [STL/CLR]"
ms.assetid: 79a14142-a528-49ab-b4fd-340f5a4e70f9
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# multimap::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計數項目的數目。  
  
## 語法  
  
```  
size_type size();  
```  
  
## 備註  
 成員函式傳回受控制序列的長度。  您可用它來決定受控制序列中目前的項目數目。  如果您只想知道序列的大小是否非零，請參閱 [multimap::empty](../dotnet/multimap-empty-stl-clr.md)`()`。  
  
## 範例  
  
```  
// cliext_multimap_size.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymultimap::make_value(L'd', 4));   
    c1.insert(Mymultimap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0 after clearing**  
**size\(\) \= 2 after adding 2**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::empty](../dotnet/multimap-empty-stl-clr.md)