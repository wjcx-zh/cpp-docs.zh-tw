---
title: "hash_map::key_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::key_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_type 成員 [STL/CLR]"
ms.assetid: 1e7d0f40-03e0-4413-b652-1d9fe14f0f12
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::key_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

排序索引鍵的類型。  
  
## 語法  
  
```  
typedef Key key_type;  
```  
  
## 備註  
 此型別是個範本參數 `Key`之同義資料表。  
  
## 範例  
  
```  
// cliext_hash_map_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_map::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::key\_compare](../dotnet/hash-map-key-compare-stl-clr.md)   
 [hash\_map::mapped\_type](../dotnet/hash-map-mapped-type-stl-clr.md)   
 [hash\_map::value\_type](../dotnet/hash-map-value-type-stl-clr.md)