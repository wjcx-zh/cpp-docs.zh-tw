---
title: "hash_map::rend (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_map::rend"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rend 成員 [STL/CLR]"
ms.assetid: 87fb2a06-c92b-4d86-855d-22f5c04aabdb
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_map::rend (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定已還原的受控制序列結尾。  
  
## 語法  
  
```  
reverse_iterator rend();  
```  
  
## 備註  
 成員函式傳回在受控制序列的開頭之外按的反向迭代器。  因此，它會指定反向序列的 `end`。  您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。  
  
## 範例  
  
```  
// cliext_hash_map_rend.cpp   
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
    Myhash_map::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**\*\-\- \-\-rend\(\) \= \[b 2\]**  
**\*\-\-型別 \(\) \= \[a 1\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)   
 [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)   
 [hash\_map::rbegin](../dotnet/hash-map-rbegin-stl-clr.md)