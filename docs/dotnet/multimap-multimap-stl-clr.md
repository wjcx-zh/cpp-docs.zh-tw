---
title: "multimap::multimap (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap 成員 [STL/CLR]"
ms.assetid: cdf9c5dc-774c-424e-aeea-7554643e401c
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
multimap();  
explicit multimap(key_compare^ pred);  
multimap(multimap<Key, Mapped>% right);  
multimap(multimap<Key, Mapped>^ right);  
template<typename InIter>  
    multimapmultimap(InIter first, InIter last);  
template<typename InIter>  
    multimap(InIter first, InIter last,  
        key_compare^ pred);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### 參數  
 首先  
 要插入的範圍開頭。  
  
 last  
 插入範圍結尾。  
  
 pred  
 受控制序列的預先定義的述詞。  
  
 right  
 物件或範圍要插入。  
  
## 備註  
 建構函式:  
  
 `multimap();`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞則為 `key_compare()`。  您會用它來指定一個空的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `explicit multimap(key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，與定序述詞則為 `pred`。  您會用它來指定一個空的初始控制序列，以指定的順序述詞。  
  
 建構函式:  
  
 `multimap(multimap<Key, Mapped>% right);`  
  
 使用序列 `[``right``.`[multimap::begin](../dotnet/multimap-begin-stl-clr.md)`(),``right``.`與預設定序述詞的[multimap::end](../dotnet/multimap-end-stl-clr.md)`())`的控制項，序列。  您會用它來指定要複製順序由多重對應物件 `right`的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `multimap(multimap<Key, Mapped>^ right);`  
  
 使用序列 `[``right``->`[multimap::begin](../dotnet/multimap-begin-stl-clr.md)`(),``right``->`與預設定序述詞的[multimap::end](../dotnet/multimap-end-stl-clr.md)`())`的控制項，序列。  您會用它來指定要複製順序由多重對應物件 `right`的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last);`  
  
 使用序列 `[``first``,`與預設定序述詞的`last`相關聯之`)`的控制項，序列。  您會用它來做受控制序列複製另一個序列，與預設定序述詞。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 使用序列 `[``first`與`,`定序述詞 `pred`之`last`相關聯之`)`的控制項，序列。  您會用它來做受控制序列複製另一個序列，以指定的順序述詞。  
  
 建構函式:  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化具有預設定序述詞的列舉值所指定的控制項順序則為 `right`。  您會用它來做受控制序列的列舉值所描述的複製另一個序列中，有預設定序的述詞。  
  
 建構函式:  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化具有定序述詞的 `pred`列舉值所指定的控制項順序則為 `right`。  您會用它來做受控制序列的列舉值所描述的複製另一個序列，以指定的順序述詞的。  
  
## 範例  
  
```  
// cliext_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
// construct an empty container   
    Mymultimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultimap c3(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3);   
    for each (Mymultimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultimap c7(c4);   
    for each (Mymultimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymultimap c8(%c3);   
    for each (Mymultimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **大小 \(\) \= 0**  
 **\[1\] \[2\] \[bc 3\]**  
**大小 \(\) \= 0**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[c 3\] \[2\] \[b 以 1\]**  
 **\[1\] \[2\] \[bc 3\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)