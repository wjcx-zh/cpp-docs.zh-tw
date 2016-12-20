---
title: "vector::vector (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector 成員 [STL/CLR]"
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::vector (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 參數  
 count  
 要插入的元素數目。  
  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 right  
 要插入的物件或範圍 。  
  
 val  
 要插入的元素值。  
  
## 備註  
 建構函式:  
  
 `vector();`  
  
 初始化受控制序列沒有項目。  您會用它來指定一個空的初始控制順序。  
  
 建構函式:  
  
 `vector(vector<Value>% right);`  
  
 使用序列 `[``right``.`[vector::begin](../dotnet/vector-begin-stl-clr.md)`(),` `right``.`[vector::end](../dotnet/vector-end-stl-clr.md)`())`的控制順序。  您會用它來指定要複製順序以向量物件 `right`的初始控制順序。  
  
 建構函式:  
  
 `vector(vector<Value>^ right);`  
  
 使用序列 `[``right``->`[vector::begin](../dotnet/vector-begin-stl-clr.md)`(),` `right``->`[vector::end](../dotnet/vector-end-stl-clr.md)`())`的控制順序。  您會用它來指定要複製順序以向量物件 `right`的初始控制順序。  
  
 建構函式:  
  
 `explicit vector(size_type count);`  
  
 使用 `count` 項目受控制序列的每個 `value_type()`值。  您可以使用它以項目填滿容器有的所有預設值。  
  
 建構函式:  
  
 `vector(size_type count, value_type val);`  
  
 使用 `count` 項目受控制序列的每個 `val`值。  您可以使用它以項目填滿容器有的所有相同值。  
  
 建構函式:  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 使用序列 `[``first``,` `last``)`的控制順序。  您會用它來做受控制序列複製另一個序列。  
  
 建構函式:  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 使用列舉值所指定的順序顯示 `right`。  您會用它來做受控制序列列舉值所描述的複製另一個序列。  
  
## 範例  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0**  
 **x x x x x x**  
 **x x x x x**  
 **x x x x x x**  
 **x x x x x x**  
 **x x x x x x**   
## 需求  
 **標頭：** \<cliext\/vector\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [向量](../dotnet/vector-stl-clr.md)   
 [vector::assign](../dotnet/vector-assign-stl-clr.md)   
 [vector::generic\_container](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)