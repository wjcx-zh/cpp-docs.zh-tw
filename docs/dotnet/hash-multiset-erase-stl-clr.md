---
title: "hash_multiset::erase (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase 成員 [STL/CLR]"
ms.assetid: bddd329d-aece-4b93-8355-005351c3aa45
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multiset::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除指定位置的項目。  
  
## 語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### 參數  
 首先  
 要清除之範圍的開頭。  
  
 Key \- 索引鍵  
 要清除的索引鍵值。  
  
 last  
 要清除之範圍結尾。  
  
 where  
 要清除的元素。  
  
## 備註  
 第 10% 成員函式中將維持在項目外的第一個項目中移除受控制序列的項目所指向的 `where`，並傳回 Iterator，或 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()` ，如果沒有此類項目存在則為。  您會用它來移除單一項目。  
  
 第二 \+ 成成員函式中受控制序列的項目。將保持在所有項目外的第一個項目被移除的範圍 `[``first``,``last``)`，並傳回 Iterator，則為 `end()` ，如果沒有此類項目存在則為。  您會用它來移除零或多個連續的項目。  
  
 第三 \+ 成成員函式中的索引鍵相同 Bucket 的項目為 `key`控制項序列的所有項目，並傳回項目數的計數中移除的。  您會用它來移除和計數符合指定索引鍵的項目。  
  
 每個項目所花費的時間比例與項目數目的對數超過受控制序列的。  
  
## 範例  
  
```  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**清除 \(啟動 \(\)\)\= b**  
 **b c d e**  
**清除 \(啟動 \(\)， end\(\)\-1\) \= e**  
**大小 \(\) \= 1**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::clear](../dotnet/hash-multiset-clear-stl-clr.md)