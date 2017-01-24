---
title: "hash_multimap::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: 51cd98b0-c959-4a44-b914-582c00681bd7
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加入項目。  
  
## 語法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### 參數  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 right  
 要插入的列舉。  
  
 val  
 要插入的值。  
  
 where  
 在容器內要插入的位置 \(僅限提示\)。  
  
## 備註  
 每一個成員函式插入由其他運算元指定的序列。  
  
 第一個成員函式插入具有 `val` 值的項目，並傳回會指定新插入項目的迭代器。  您可用它來插入單一項目。  
  
 第二個成員函式插入具有值 `val` 的項目 \(使用 `where` 做為提示，以改善效能\)，並傳回指定新插入項目的迭代器。  您可用它來插入一個已知項目的相鄰項目。  
  
 第三個成員函式插入序列 `[``first``,` `last``)`。  您可用它插入從另一個序列複製的零或多個項目。  
  
 第四個成員函式插入 `right` 指定的序列。  您可用它來插入列舉程式描述的序列。  
  
 每個項目插入所需花費的時間與受控制序列中的項目數之對數成比例。  插入會發生在分期的常數時間中，但是將給定指出相鄰於插入點項目的提示。  
  
## 範例  
  
```  
// cliext_hash_multimap_insert.cpp   
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
  
// insert a single value, unique and duplicate   
    Myhash_multimap::iterator it =   
        c1.insert(Myhash_multimap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",   
        it->first, it->second);   
  
    it = c1.insert(Myhash_multimap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",   
        it->first, it->second);   
  
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    it = c1.insert(c1.begin(), Myhash_multimap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multimap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multimap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Myhash_multimap::value_type>^)%c1);   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**insert\(\[L'x' 24\]\) \= \[x 24\]**  
**insert\(\[L'b' 2\]\) \= \[b 2\]**  
 **\[a 1\] \[b 2\] \[b 2\] \[c 3\] \[x 24\]**  
**insert\(begin\(\), \[L'y' 25\]\) \= \[y 25\]**  
 **\[a 1\] \[b 2\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**  
 **\[a 1\] \[b 2\] \[b 2\] \[c 3\] \[x 24\]**  
 **\[a 1\] \[b 2\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)