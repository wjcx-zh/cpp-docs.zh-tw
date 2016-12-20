---
title: "pair::pair (STL/CLR) | Microsoft Docs"
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
  - "cliext::pair::pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pair 成員 [STL/CLR]"
ms.assetid: 188035f3-bd37-4b46-96dd-5ceb9a16df79
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# pair::pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構一對物件。  
  
## 語法  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### 參數  
 right  
 儲存的一組。  
  
 val1  
 儲存的第一個值。  
  
 val2  
 儲存的第二個值。  
  
## 備註  
 建構函式:  
  
 `pair();`  
  
 初始化使用預設建構之值的已儲存組。  
  
 建構函式:  
  
 `pair(pair<Value1, Value2>% right);`  
  
 使用 `right`和`.`[pair::first](../dotnet/pair-first-stl-clr.md) `right`[pair::second](../dotnet/pair-second-stl-clr.md)`.`的已儲存組來初始化。  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 使用 `right`和`->`[pair::first](../dotnet/pair-first-stl-clr.md) `right`[pair::second](../dotnet/pair-second-stl-clr.md)`>`的已儲存組來初始化。  
  
 建構函式:  
  
 `pair(Value1 val1, Value2 val2);`  
  
 使用 `val1` 和 `val2` 初始化儲存組。  
  
## 範例  
  
```  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
  **\[\\0, 0\]**  
**\[x, 3\]**  
**\[x, 3\]**  
**\[x, 3\]**   
## 需求  
 **標頭 ：** \<cliext\/utility\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [pair](../dotnet/pair-stl-clr.md)