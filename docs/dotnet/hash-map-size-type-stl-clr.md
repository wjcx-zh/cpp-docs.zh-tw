---
title: "hash_map::size_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::size_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_type 成員 [STL/CLR]"
ms.assetid: 062901e1-b52b-41e4-81be-b6646879e22a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::size_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

兩個項目之間的帶正負號距離的類型。  
  
## 語法  
  
```  
typedef int size_type;  
```  
  
## 備註  
 描述非負數項目計數的型別。  
  
## 範例  
  
```  
// cliext_hash_map_size_type.cpp   
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
  
// compute positive difference   
    Myhash_map::size_type diff = 0;   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**end\(\)\-begin\(\) \= 3**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::empty](../dotnet/hash-map-empty-stl-clr.md)