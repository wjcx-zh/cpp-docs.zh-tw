---
title: "hash_multiset::upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound 成員 [STL/CLR]"
ms.assetid: d5be0d79-ae60-42bb-8a53-051bc374407d
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_multiset::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

符合指定之索引鍵的範圍中尋找結尾。  
  
## 語法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### 參數  
 Key \- 索引鍵  
 要搜尋的索引鍵值。  
  
## 備註  
 成員函式來判斷在個項目且雜湊至與 `key` 相同 Bucket 的項目 `key`的受控制序列的最後一個項目的 `X` 。  如果沒有這類項目，則為，如果 `X` 是在受控制序列的最後一個項目，則會傳回 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()`;否則會指定在 `X`之外的第一個項目的 Iterator 傳回它。  您可以使用它目前所在項目的結尾符合指定索引鍵受控制序列。  
  
## 範例  
  
```  
// cliext_hash_multiset_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**upper\_bound \(L'x\) \=\=end \(\) \= true**  
**\*upper\_bound \(L'a \= b\)**  
**\*upper\_bound \(L'b\) \= c**   
## 需求  
 **標題:** \<cliext\/hash\_set\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::count](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash\_multiset::equal\_range](../dotnet/hash-multiset-equal-range-stl-clr.md)   
 [hash\_multiset::find](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)