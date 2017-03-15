---
title: "hash_multiset::hash_multiset (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::hash_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multiset 成員 [STL/CLR]"
ms.assetid: 1b224c60-b714-4ed5-9234-79b61b92a953
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_multiset::hash_multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_multiset();`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `key_compare()`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，與預設定序述詞和雜湊函數。  
  
 建構函式:  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `pred`以及預設的雜湊函式。  您會用它來指定一個空的初始控制序列，與指定定序述詞和預設雜湊函數。  
  
 建構函式:  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞 `pred`以及雜湊函式`hashfn`。  您會用它來指定一個空的初始控制序列，與指定定序述詞和雜湊函數。  
  
 建構函式:  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``right``.`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``.`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`，使用預設定序述詞以及預設的雜湊函式。  您會用它來指定為由雜湊組合物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``right``->`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``->`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`，使用預設定序述詞以及預設的雜湊函式。  您會用它來指定為由雜湊組合物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)`，使用預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，與預設定序述詞和雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)``pred`，使用預設定序述詞以及預設的雜湊函式。  您會用它來做受控制序列複製另一個序列，與指定定序述詞和預設雜湊函式。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制序列中沒有項目，使用序列 `[``first``,` `last``)``pred`，使用預設定序述詞以及預設的雜湊函式`hashfn`。  您會用它來做受控制序列複製另一個序列，與指定定序述詞和雜湊函式。  
  
 建構函式:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞以及預設的雜湊函式。  您會用它加上預設定序述詞來作為列舉值所描述的另一個序列複製的控制序列和雜湊函式。  
  
 建構函式:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞`pred`以及預設的雜湊函式。  您會用它加上指定序述詞來作為列舉值所描述的另一個序列複製的控制序列和預設雜湊函式。  
  
 建構函式:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 初始化控制序列與列舉值所指定的 `right`序列，與預設定序述詞`pred`以及預設的雜湊函式`hashfn`。  您會用它加上指定定序述詞來作為列舉值所描述的另一個序列複製的控制序列和雜湊函式。  
  
## 範例  
  
```  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **c b a**  
 **a b c**  
 **a b c**  
 **c b a**  
 **a b c**  
 **a b c**  
 **c b a**  
 **a b c**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/hash\_set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)