---
title: "hash_multimap::erase (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成員 [STL/CLR]"
ms.assetid: 663c67f6-8070-47db-abdc-58f7ace69736
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置的項目。  
  
## 語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### 參數  
 first  
 要清除之範圍的開頭。  
  
 Key \- 索引鍵  
 要清除的索引鍵值。  
  
 last  
 要清除之範圍的結尾。  
  
 where  
 要清除的項目。  
  
## 備註  
 第一個成員函式移除受控制序列中 `where` 指向的項目，並且回傳迭代器，其委派移除的項目之上的第一個剩餘項目，若沒有這樣的項目存在則傳回 [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`()`。  您可用它來移除單一項目。  
  
 第二個成員函式移除受控制序列中範圍 `[``first``,` `last``)` 的項目，並且傳回迭代器，其委派移除的任何項目之上的第一個剩餘項目，若沒有這樣的項目存在則傳回 `end()`。  您可用它來移除零或多個連續的項目。  
  
 第三個成員函式移除受控制序列中擁有和 `key` 相等排序的索引值的任何項目，並且回傳移除的項目數。  您可用它來移除和計數符合指定索引鍵的項目。  
  
 每個項目消除所需花費的時間與受控制序列中的項目數之對數成比例。  
  
## 範例  
  
```  
// cliext_hash_multimap_erase.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    cliext::hash_multimap<wchar_t, int> c1;   
    c1.insert(cliext::hash_multimap<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::hash_multimap<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::hash_multimap<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::hash_multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::hash_multimap<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::hash_multimap<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::hash_multimap<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::hash_multimap<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**erase\(begin\(\)\) \= \[b 2\]**  
 **\[b 2\] \[c 3\] \[d 4\] \[e 5\]**  
**erase\(begin\(\), end\(\)\-1\) \= \[e 5\]**  
**size\(\) \= 1**  
**erase\(L'x'\) \= 0**  
**erase\(L'e'\) \= 1**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::clear](../dotnet/hash-multimap-clear-stl-clr.md)