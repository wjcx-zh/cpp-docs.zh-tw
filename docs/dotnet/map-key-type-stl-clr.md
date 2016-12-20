---
title: "map::key_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::key_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_type 成員 [STL/CLR]"
ms.assetid: 5bcf92e4-d9ff-48a2-86da-e24842ccf80c
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::key_type (STL/CLR)
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
// cliext_map_key_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Mymap::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標頭：** \<cliext\/map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [map](../dotnet/map-stl-clr.md)   
 [map::key\_compare](../dotnet/map-key-compare-stl-clr.md)   
 [map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)   
 [map::value\_type](../dotnet/map-value-type-stl-clr.md)