---
title: "hash_map::make_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value 成員 [STL/CLR]"
ms.assetid: 1fcdcacc-5edf-46b7-9481-9a4aef32b025
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::make_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個值物件。  
  
## 語法  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要使用的索引鍵值。  
  
 已對應  
 要進行搜尋的對應值。  
  
## 備註  
 成員函式傳回索引鍵為 `key` ，並將值為 `mapped`的 `value_type` 物件。  您可用它來撰寫適用於與其他數種成員函式一起使用的物件。  
  
## 範例  
  
```  
// cliext_hash_map_make_value.cpp   
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
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::key\_type](../dotnet/hash-map-key-type-stl-clr.md)   
 [hash\_map::mapped\_type](../dotnet/hash-map-mapped-type-stl-clr.md)   
 [hash\_map::value\_type](../dotnet/hash-map-value-type-stl-clr.md)