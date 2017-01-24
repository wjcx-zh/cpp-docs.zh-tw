---
title: "range_adapter::range_adapter (STL/CLR) | Microsoft Docs"
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
  - "cliext::range_adapter::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter 成員 [STL/CLR]"
ms.assetid: b16af13f-3358-4e82-927d-d0d4986bcb18
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# range_adapter::range_adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構配接器物件。  
  
## 語法  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### 參數  
 first  
 要包裝的第一個迭代器。  
  
 last  
 第二個要包裝的迭代器。  
  
 right  
 要複製的物件。  
  
## 備註  
 建構函式:  
  
 `range_adapter();`  
  
 使用預設已建構的迭代器初始化已儲存的迭代器。  
  
 建構函式:  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 透過複製儲存在 `right`中的迭代器對初始化已儲存的迭代器。  
  
 建構函式:  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 透過複製儲存在 `*right`中的迭代器對初始化已儲存的迭代器。  
  
 建構函式:  
  
 `range_adapter(Iter^ first, last);`  
  
 使用 `first` 和 `last` 初始化儲存的迭代器。  
  
## 範例  
  
```  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **a b c**   
## 需求  
 **標頭:** \<cliext\/adapter\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)   
 [range\_adapter::operator\=](../dotnet/range-adapter-operator-assign-stl-clr.md)