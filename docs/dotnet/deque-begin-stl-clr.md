---
title: "deque::begin (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin 成員 [STL/CLR]"
ms.assetid: e99d20d2-bb33-415f-9bd6-fe331d8c2ba2
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控制序列的開頭。  
  
## 語法  
  
```  
iterator begin();  
```  
  
## 備註  
 指定受控制序列的第一個項目的成員函式會傳回隨機存取 Iterator，或只是超出空序列的結尾。  您要用它來取得的 Iterator 可指定受控制序列之 `current` 開頭，但是，如果受控制序列的長度變更，它的狀態也可以變更。  
  
## 範例  
  
```  
// cliext_deque_begin.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*begin \(\=\)。**  
**\*\+\+begin \(\) \= b**  
 **x\-y c**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::end](../dotnet/deque-end-stl-clr.md)   
 [deque::front](../dotnet/deque-front-stl-clr.md)   
 [deque::front\_item](../dotnet/deque-front-item-stl-clr.md)