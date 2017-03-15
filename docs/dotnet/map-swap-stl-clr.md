---
title: "map::swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 成員 [STL/CLR]"
ms.assetid: b36ed982-21ce-40e5-9636-ecdbaf1b7eec
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# map::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交換兩個容器的內容。  
  
## 語法  
  
```  
void swap(map<Key, Mapped>% right);  
```  
  
#### 參數  
 right  
 要交換內容的容器。  
  
## 備註  
 成員函式交換在 `this` 和 `right`的控制順序。  它在常數時間執行，而且不會擲回例外狀況。  您將它當做一個快速的方法交換兩個容器的內容。  
  
## 範例  
  
```  
// cliext_map_swap.cpp   
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
  
// construct another container with repetition of values   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'd', 4));   
    c2.insert(Mymap::make_value(L'e', 5));   
    c2.insert(Mymap::make_value(L'f', 6));   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
 **d \[4\] \[5\] \[ef 6\]**  
 **d \[4\] \[5\] \[ef 6\]**  
 **\[1\] \[2\] \[bc 3\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::operator\=](../dotnet/map-operator-assign-stl-clr.md)