---
title: "map::map (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "map 成員 [STL/CLR]"
ms.assetid: c91f699a-4742-4859-b2b3-c2a01a750bea
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `map();`  
  
 初始化受控制序列中沒有項目，使用預設定序述詞則為 `key_compare()`。  您會用它來指定一個空的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `explicit map(key_compare^ pred);`  
  
 初始化受控制序列中沒有項目，與定序述詞則為 `pred`。  您會用它來指定一個空的初始控制序列，以指定的順序述詞。  
  
 建構函式:  
  
 `map(map<Key, Mapped>% right);`  
  
 使用序列 `[``right``.`[map::begin](../dotnet/map-begin-stl-clr.md)`(),``right``.`與預設定序述詞的[map::end](../dotnet/map-end-stl-clr.md)`())`的控制項，序列。  您會用它來指定要複製順序由對應 `right`物件的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `map(map<Key, Mapped>^ right);`  
  
 使用序列 `[``right``->`[map::begin](../dotnet/map-begin-stl-clr.md)`(),``right``->`與預設定序述詞的[map::end](../dotnet/map-end-stl-clr.md)`())`的控制項，序列。  您會用它來指定要複製順序由對應 `right`物件的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `map(InIter first, InIter last);`  
  
 使用序列 `[``first``,`與預設定序述詞的`last`相關聯之`)`的控制項，序列。  您會用它來做受控制序列複製另一個序列，與預設定序述詞。  
  
 建構函式:  
  
 `template<typename InIter>`  
  
 `map(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 使用序列 `[``first`與`,`定序述詞 `pred`之`last`相關聯之`)`的控制項，序列。  您會用它來做受控制序列複製另一個序列，以指定的順序述詞。  
  
 建構函式:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化具有預設定序述詞的列舉值所指定的控制項順序則為 `right`。  您會用它來做受控制序列的列舉值所描述的複製另一個序列中，有預設定序的述詞。  
  
 建構函式:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 初始化具有定序述詞的 `pred`列舉值所指定的控制項順序則為 `right`。  您會用它來做受控制序列的列舉值所描述的複製另一個序列，以指定的順序述詞的。  
  
## 範例  
  
```  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
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
 [map](../dotnet/map-stl-clr.md)   
 [map::generic\_container](../dotnet/map-generic-container-stl-clr.md)   
 [map::operator\=](../dotnet/map-operator-assign-stl-clr.md)