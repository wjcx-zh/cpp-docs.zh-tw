---
title: "hash_map::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert 成員 [STL/CLR]"
ms.assetid: 52926ec7-ad4e-4791-a043-46136ee40a69
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加入項目。  
  
## 語法  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 第一個成員函式竭力插入具有值 `val` 的元素，並傳回一對值 `X`。  如果 `X.second` 為 true，`X.first` 會指定新插入的項目；否則 `X.first` 會指定具有已經存在之相等排序的項目，且不會插入新項目。  您可用它來插入單一項目。  
  
 第二個成員函式插入具有值 `val` 的項目 \(使用 `where` 做為提示，以改善效能\)，並傳回指定新插入項目的迭代器。  您可用它來插入一個已知項目的相鄰項目。  
  
 第三個成員函式插入序列 `[``first``,` `last``)`。  您可用它插入從另一個序列複製的零或多個項目。  
  
 第四個成員函式插入 `right` 指定的序列。  您可用它來插入列舉程式描述的序列。  
  
 每個項目插入所需花費的時間與受控制序列中的項目數之對數成比例。  插入會發生在分期的常數時間中，但是將給定指出相鄰於插入點項目的提示。  
  
## 範例  
  
```  
// cliext_hash_map_insert.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
typedef Myhash_map::pair_iter_bool Pairib;   
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
  
// insert a single value, unique and duplicate   
    Pairib pair1 =   
        c1.insert(Myhash_map::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Myhash_map::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Myhash_map::iterator it =   
        c1.insert(c1.begin(), Myhash_map::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_map c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_map c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Myhash_map::value_type>^)%c1);   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[a 1\] \[b 2\] \[c 3\]**  
**insert\(\[L'x' 24\]\) \= \[x 24\] True**  
**insert\(\[L'b' 2\]\) \= \[b 2\] False**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\]**  
**insert\(begin\(\), \[L'y' 25\]\) \= \[y 25\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\]**  
 **\[a 1\] \[b 2\] \[c 3\] \[x 24\] \[y 25\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)