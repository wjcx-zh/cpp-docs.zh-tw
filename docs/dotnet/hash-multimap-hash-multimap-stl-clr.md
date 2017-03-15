---
title: "hash_multimap::hash_multimap (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::hash_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multimap 成員 [STL/CLR]"
ms.assetid: a1d576a7-5dc7-4ad9-abef-ee7a13caaec3
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::hash_multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
hash_multimap();  
explicit hash_multimap(key_compare^ pred);  
hash_multimap(key_compare^ pred, hasher^ hashfn);  
hash_multimap(hash_multimap<Key, Mapped>% right);  
hash_multimap(hash_multimap<Key, Mapped>^ right);  
template<typename InIter>  
    hash_multimaphash_multimap(InIter first, InIter last);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### 參數  
 first  
 要插入的範圍開頭。  
  
 hashfn  
 對應的金鑰雜湊函式到 Bucket。  
  
 last  
 要插入的範圍結尾。  
  
 pred  
 為控制序列預先定義的述詞。  
  
 right  
 要插入的物件或範圍 。  
  
## 備註  
 建構函式:  
  
 `hash_multimap();`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `key_compare()`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，與預設定序述詞和雜湊函數。  
  
 建構函式:  
  
 `explicit hash_multimap(key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `pred`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，與指定定序述詞和預設雜湊函數。  
  
 建構函式:  
  
 `hash_multimap(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `pred`以及雜湊函式`hashfn`。  您會用它來指定一個空的初始控制序列，與指定定序述詞和雜湊函數。  
  
 建構函式:  
  
 `hash_multimap(hash_multimap<Key, Mapped>% right);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``right``.`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``.`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`，使用預設定序述詞以及預設的雜湊函式。  您會用它來指定為由雜湊multimap物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_multimap(hash_multimap<Key, Mapped>^ right);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``right``->`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``->`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`，使用預設定序述詞以及預設的雜湊函式。  您會用它來指定為由雜湊multimap物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)`，使用預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，與預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)``pred`，使用預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，與指定定序述詞和預設雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)``pred`，使用預設定序述詞以及預設的雜湊函式`hashfn`。  您會用它來做受控制序列複製另一個序列，與指定定序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞以及預設的雜湊函式。  您會用它加上預設定序述詞來作為列舉值所描述的另一個序列複製的控制序列和雜湊函式。  
  
 建構函式:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞`pred`以及預設的雜湊函式。  您會用它加上指定序述詞來作為列舉值所描述的另一個序列複製的控制序列和預設雜湊函式。  
  
 建構函式:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞`pred`以及預設的雜湊函式`hashfn`。  您會用它加上指定定序述詞來作為列舉值所描述的另一個序列複製的控制序列和雜湊函式。  
  
## 範例  
  
```  
// cliext_hash_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
// construct an empty container   
    Myhash_multimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multimap c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multimap c3(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multimap c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3);   
    for each (Myhash_multimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multimap c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multimap c7(c4);   
    for each (Myhash_multimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_multimap c8(%c3);   
    for each (Myhash_multimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[a 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[a 1\]**  
 **\[a 1\] \[b 2\] \[c 3\]**  
 **\[a 1\] \[b 2\] \[c 3\]**   
## 需求  
 **標頭：** \<cliext\/hash\_map\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::generic\_container](../dotnet/hash-multimap-generic-container-stl-clr.md)   
 [hash\_multimap::operator\=](../dotnet/hash-multimap-operator-assign-stl-clr.md)