---
title: "hash_multimap::upper_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成員 [STL/CLR]"
ms.assetid: 4fa58df6-63ec-411d-bcf9-301d3c88569a
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

尋找符合指定之索引鍵的範圍結尾。  
  
## 語法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引值。  
  
## 備註  
 成員函式指定受控制序列中最後一個`X`雜湊至與 `key` 相同 Bucket 的項目，以及與 `key` 相等排序的項目。  如果沒有這類項目，或如果 `X` 是在受控制序列的最後一個項目，則會傳回 [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`()`;否則會指定在 `X`之外的第一個項目的 Iterator 傳回它。  您可以使用它目前所在項目的結尾符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_hash_multimap_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_multimap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**upper\_bound \(L'x\) \=\=end \(\) \= true**  
**\*upper\_bound\(L'a'\) \= \[b 2\]**  
**\*upper\_bound\(L'b'\) \= \[c 3\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::count](../dotnet/hash-multimap-count-stl-clr.md)   
 [hash\_multimap::equal\_range](../dotnet/hash-multimap-equal-range-stl-clr.md)   
 [hash\_multimap::find](../dotnet/hash-multimap-find-stl-clr.md)   
 [hash\_multimap::lower\_bound](../dotnet/hash-multimap-lower-bound-stl-clr.md)