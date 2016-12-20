---
title: "hash_map::hash_map (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map 成員 [STL/CLR]"
ms.assetid: d65eb3fa-4bf9-4186-95f8-5517c90ef1fa
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::hash_map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
hash_map();  
explicit hash_map(key_compare^ pred);  
hash_map(key_compare^ pred, hasher^ hashfn);  
hash_map(hash_map<Key, Mapped>% right);  
hash_map(hash_map<Key, Mapped>^ right);  
template<typename InIter>  
    hash_maphash_map(InIter first, InIter last);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### 參數  
 首先  
 要插入的範圍開頭。  
  
 hashfn  
 對應的金鑰雜湊函式到 Bucket。  
  
 last  
 插入範圍結尾。  
  
 pred  
 受控制序列的預先定義的述詞。  
  
 right  
 物件或範圍要插入。  
  
## 備註  
 建構函式:  
  
 `hash_map();`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `key_compare()`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，與預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `explicit hash_map(key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，與定序述詞 `pred`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，以指定的順序述詞以及預設的雜湊函式。  
  
 建構函式:  
  
 `hash_map(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制序列中沒有項目，與定序述詞 `pred`和雜湊函式 `hashfn`。  您會用它來指定一個空的初始控制序列，以指定的順序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_map(hash_map<Key, Mapped>% right);`  
  
 初始化控制序列與序列 `[``right``.`[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)`(),``right``.`[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`())`，具有預設定序述詞以及預設的雜湊函式。  您會用它來指定要複製順序由與預設定序述詞和雜湊函式的 `right`， hash\_map 物件的初始控制順序。  
  
 建構函式:  
  
 `hash_map(hash_map<Key, Mapped>^ right);`  
  
 初始化控制序列與序列 `[``right``->`[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)`(),``right``->`[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`())`，具有預設定序述詞以及預設的雜湊函式。  您會用它來指定要複製順序由與預設定序述詞和雜湊函式的 `right`， hash\_map 物件的初始控制順序。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last);`  
  
 初始化控制序列與序列 `[``first``,``last``)`，具有預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，與預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列與序列 `[``first``,``last``)`，與定序述詞 `pred`以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，以指定的順序述詞以及預設的雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_map(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列與序列 `[``first``,``last``)`，與定序述詞 `pred`和雜湊函式 `hashfn`。  您會用它來做受控制序列複製另一個序列，以指定的順序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列的列舉值所描述的複製另一個序列中，有預設定序述詞和雜湊函式的。  
  
 建構函式:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列與列舉值所指定的順序，與 `right`定序述詞 `pred`以及預設的雜湊函式。  您會用它來做受控制序列的列舉值所描述的複製另一個序列，以指定的順序述詞和預設雜湊函式的。  
  
 建構函式:  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列與列舉值所指定的順序，與 `right`定序述詞 `pred`和雜湊函式 `hashfn`。  您會用它來做受控制序列的列舉值所描述的複製另一個序列，以指定的順序述詞和雜湊函式的。  
  
## 範例  
  
```  
// cliext_hash_map_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
// construct an empty container   
    Myhash_map c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_map c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_map c3(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_map c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_map c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_map c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3);   
    for each (Myhash_map::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_map c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_map c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_map c7(c4);   
    for each (Myhash_map::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_map c8(%c3);   
    for each (Myhash_map::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **大小 \(\) \= 0**  
 **\[1\] \[2\] \[bc 3\]**  
**大小 \(\) \= 0**  
 **\[1\] \[2\] \[bc 3\]**  
**大小 \(\) \= 0**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[1\] \[2\] \[bc 3\]**   
## 需求  
 **標題:** \<cliext\/hash\_map\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::generic\_container](../dotnet/hash-map-generic-container-stl-clr.md)   
 [hash\_map::operator\=](../dotnet/hash-map-operator-assign-stl-clr.md)