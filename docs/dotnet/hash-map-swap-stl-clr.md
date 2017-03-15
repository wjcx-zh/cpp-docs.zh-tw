---
title: "hash_map::swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_map::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 成員 [STL/CLR]"
ms.assetid: bc1349e0-9be2-4767-a87b-4834615cb52a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# hash_map::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

交換兩個容器的內容。  
  
## 語法  
  
```  
void swap(hash_map<Key, Mapped>% right);  
```  
  
#### 參數  
 right  
 要交換內容的容器。  
  
## 備註  
 成員函式交換在 `this` 和 `right`的控制順序。  它在常數時間執行，而且不會擲回例外狀況。  您將它當做一個快速的方法交換兩個容器的內容。  
  
## 範例  
  
```  
// cliext_hash_map_swap.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_map c2;   
    c2.insert(Myhash_map::make_value(L'd', 4));   
    c2.insert(Myhash_map::make_value(L'e', 5));   
    c2.insert(Myhash_map::make_value(L'f', 6));   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Myhash_map::value_type elem in c2)   
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
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::operator\=](../dotnet/hash-map-operator-assign-stl-clr.md)