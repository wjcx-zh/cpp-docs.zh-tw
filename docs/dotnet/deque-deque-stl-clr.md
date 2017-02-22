---
title: "deque::deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque 成員 [STL/CLR]"
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# deque::deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一個容器物件。  
  
## 語法  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### 參數  
 count  
 插入的項目數目。  
  
 首先  
 要插入的範圍開頭。  
  
 last  
 插入範圍結尾。  
  
 right  
 物件或範圍要插入。  
  
 val  
 要插入的元素值。  
  
## 備註  
 建構函式:  
  
 `deque();`  
  
 初始化受控制序列沒有項目。  您會用它來指定一個空的初始控制順序。  
  
 建構函式:  
  
 `deque(deque<Value>% right);`  
  
 使用序列 `[``right``.`[deque::begin](../dotnet/deque-begin-stl-clr.md)`(),``right``.`[deque::end](../dotnet/deque-end-stl-clr.md)`())`的控制順序。  您會用它來指定要複製順序由雙向佇列物件 `right`的初始控制順序。  
  
 建構函式:  
  
 `deque(deque<Value>^ right);`  
  
 使用序列 `[``right``->`[deque::begin](../dotnet/deque-begin-stl-clr.md)`(),``right``->`[deque::end](../dotnet/deque-end-stl-clr.md)`())`的控制順序。  您會用它來指定要複製順序由雙向佇列物件的控制代碼是 `right`的初始控制順序。  
  
 建構函式:  
  
 `explicit deque(size_type count);`  
  
 使用 `count` 項目受控制序列的每個 `value_type()`值。  您可以使用它以項目填滿容器有的所有預設值。  
  
 建構函式:  
  
 `deque(size_type count, value_type val);`  
  
 使用 `count` 項目受控制序列的每個 `val`值。  您可以使用它以項目填滿容器的全部有相同的值。  
  
 建構函式:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 使用序列 `[``first``,``last``)`的控制順序。  您會用它來做受控制序列複製另一個序列。  
  
 建構函式:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 使用列舉值所指定的順序顯示 `right`。  您會用它來做受控制序列列舉值所描述的複製另一個序列。  
  
## 範例  
  
```  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **大小 \(\) \= 0**  
 **0 0 0**  
 **x x x x x x**  
 **x x x x x**  
 **x x x x x x**  
 **x x x x x x**  
 **x x x x x x**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)   
 [operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)