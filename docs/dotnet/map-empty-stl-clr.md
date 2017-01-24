---
title: "map::empty (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::empty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "empty 成員 [STL/CLR]"
ms.assetid: ce41d37a-2896-48df-87ea-d3f3b3e5ab45
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::empty (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試項目是否不存在。  
  
## 語法  
  
```  
bool empty();  
```  
  
## 備註  
 成員函式傳回 true 表示一個空的控制順序。  它與 [map::size](../dotnet/map-size-stl-clr.md)`() == 0`。  您會用它來測試對應是否是空的。  
  
## 範例  
  
```  
// cliext_map_empty.cpp   
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
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
**大小 \(\) \= 3**  
**空白 \(\) \= false**  
**大小 \(\) \= 0**  
**空白 \(\) \= true**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::size](../dotnet/map-size-stl-clr.md)