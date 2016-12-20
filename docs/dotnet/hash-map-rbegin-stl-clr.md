---
title: "hash_map::rbegin (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::rbegin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rbegin 成員 [STL/CLR]"
ms.assetid: e3b6c4d5-9482-471e-b5fc-70331b082a9b
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::rbegin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定已還原的受控制序列開頭。  
  
## 語法  
  
```  
reverse_iterator rbegin();  
```  
  
## 備註  
 成員函式來傳回指定受控制序列的最後一個項目在空序列開頭的之外的反向 Iterator，則為。  因此，它會指定反向序列的 `beginning`。  您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。  
  
## 範例  
  
```  
// cliext_hash_map_rbegin.cpp   
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
  
// inspect first two items in reversed sequence   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
**\*rbegin \(\) \= \[c 3\]**  
**\*\+\+rbegin \(\) \= \[b 2\]**   
## 需求  
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)   
 [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)   
 [hash\_map::rend](../dotnet/hash-map-rend-stl-clr.md)