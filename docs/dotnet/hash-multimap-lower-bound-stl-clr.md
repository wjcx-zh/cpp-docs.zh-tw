---
title: "hash_multimap::lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound 成員 [STL/CLR]"
ms.assetid: c61091ef-8364-4447-bdd2-a402cbc05f05
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找符合指定索引鍵的項目範圍的開頭。  
  
## 語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引鍵值。  
  
## 備註  
 成員函式來判斷在個項目且雜湊至與 `key` 相同 Bucket 的項目 `key`的受控制序列的第一個項目的 `X` 。  如果沒有此類項目存在，便會傳回 [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`()`;否則會指定 `X`的會傳回 Iterator。  您可以使用它目前所在項目的開頭符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_hash_multimap_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Myhash_multimap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[1\] \[2\] \[bc 3\]**  
**lower\_bound \(L'x\) \=\=end \(\) \= true**  
**\*lower\_bound \(L'a\) \= \[以 1\]**  
**\*lower\_bound \(L'b\) \= \[b 2\]**   
## 需求  
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::count](../dotnet/hash-multimap-count-stl-clr.md)   
 [hash\_multimap::equal\_range](../dotnet/hash-multimap-equal-range-stl-clr.md)   
 [hash\_multimap::find](../dotnet/hash-multimap-find-stl-clr.md)   
 [hash\_multimap::upper\_bound](../dotnet/hash-multimap-upper-bound-stl-clr.md)