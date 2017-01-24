---
title: "multiset::multiset (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiset 成員 [STL/CLR]"
ms.assetid: a6ddb2df-d7cd-4b12-aee7-81da1f67f57f
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
multiset();  
explicit multiset(key_compare^ pred);  
multiset(multiset<Key>% right);  
multiset(multiset<Key>^ right);  
template<typename InIter>  
    multisetmultiset(InIter first, InIter last);  
template<typename InIter>  
    multiset(InIter first, InIter last,  
        key_compare^ pred);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### 參數  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 pred  
 為控制序列預先定義的述詞。  
  
 right  
 要插入的物件或範圍 。  
  
## 備註  
 建構函式:  
  
 `multiset();`  
  
 以空項目初始化控制序列，使用預設定序述詞 `key_compare()`。  您會用它來指定一個空的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `explicit multiset(key_compare^ pred);`  
  
 以空項目初始化控制序列，使用序述詞 `pred`。  您會用它來指定一個空的初始控制序列，與指定序述詞。  
  
 建構函式:  
  
 `multiset(multiset<Key>% right);`  
  
 使用序列 `[``right``.`[multiset::begin](../dotnet/multiset-begin-stl-clr.md)`(),` `right``.`[multiset::end](../dotnet/multiset-end-stl-clr.md)`())` 與預設定序述詞初始化控制項序列。  您會用它來指定為由多重集物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞。  
  
 建構函式:  
  
 `multiset(multiset<Key>^ right);`  
  
 使用序列 `[``right``->`[multiset::begin](../dotnet/multiset-begin-stl-clr.md)`(),` `right``->`[multiset::end](../dotnet/multiset-end-stl-clr.md)`())` 與預設定序述詞初始化控制項序列。  您會用它來指定為由多重集物件 `right`控制的序列的拷貝的初始控制序列，以及預設定序述詞。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `multiset(InIter first, InIter last);`  
  
 使用序列 `[``first``,` `last``)` 與預設定序述詞初始化控制項序列。  您會用它加上預設定序述詞來為受控制序列複製另一個序列。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `multiset(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 使用序列 `[``first``,` `last``)` 與序述詞初始化控制項序列 `pred`。  您會用它加上指定序述詞來為受控制序列複製另一個序列。  
  
 建構函式:  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 由預設定序述詞加上列舉值 `right` 指定的序列初始化控制項序列。  您會用它加上預設定序述詞來作為列舉值所描述的另一個序列複製的控制序列。  
  
 建構函式:  
  
 `multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 由序述詞加上列舉值 `right` 指定的序列初始化控制項序列 `pred`。  您會用它加上指定序述詞來作為列舉值所描述的另一個序列複製的控制序列。  
  
## 範例  
  
```  
// cliext_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
// construct an empty container   
    Mymultiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mymultiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **c b a**  
 **a b c**  
 **c b a**  
 **a b c**  
 **c b a**  
 **c b a**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::generic\_container](../dotnet/multiset-generic-container-stl-clr.md)   
 [multiset::operator\=](../dotnet/multiset-operator-assign-stl-clr.md)