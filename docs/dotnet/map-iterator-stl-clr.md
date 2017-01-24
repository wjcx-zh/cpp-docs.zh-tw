---
title: "map::iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator 成員 [STL/CLR]"
ms.assetid: b2953b9b-0e6d-49f3-a28f-47d04d16d5f6
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

受控制序列中 iterator 的類型。  
  
## 語法  
  
```  
typedef T1 iterator;  
```  
  
## 備註  
 型別描述可以當做雙向 Iterator 為此控制序列未指定型別 `T1` 的物件。  
  
## 範例  
  
```  
// cliext_map_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Mymap::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::const\_iterator](../dotnet/map-const-iterator-stl-clr.md)