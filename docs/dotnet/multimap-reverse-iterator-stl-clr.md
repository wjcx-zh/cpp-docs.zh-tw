---
title: "multimap::reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator 成員 [STL/CLR]"
ms.assetid: 45ef2b07-8f5d-478c-8dcb-35bd07d3743a
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於受控制序列的反向迭代器類型。  
  
## 語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## 備註  
 此型別描述其可以為此控制序列當做反向迭代器之未指定型別 `T3` 的物件。  
  
## 範例  
  
```  
// cliext_multimap_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymultimap::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[c 3\] \[b 2\] \[a 1\]**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::const\_iterator](../dotnet/multimap-const-iterator-stl-clr.md)   
 [multimap::const\_reverse\_iterator](../dotnet/multimap-const-reverse-iterator-stl-clr.md)   
 [multimap::iterator](../dotnet/multimap-iterator-stl-clr.md)