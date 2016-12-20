---
title: "list::end (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end 成員 [STL/CLR]"
ms.assetid: c3444164-2c6e-4cbd-8765-1ce7d30fc43e
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定受控制序列的結尾。  
  
## 語法  
  
```  
iterator end();  
```  
  
## 備註  
 在受控制序列之結尾點的成員函式會傳回隨機存取 Iterator。  您會受控制序列之結尾的它來取得 Iterator;不是它的狀態 doesn 變更，如果受控制序列的長度變更。  
  
## 範例  
  
```  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
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
**\*\-\- \-\-end\(\) \= b**  
**\*\-\-結束 \(\) \= c**  
 **X\-Y**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::back](../dotnet/list-back-stl-clr.md)   
 [list::back\_item](../dotnet/list-back-item-stl-clr.md)   
 [list::begin](../dotnet/list-begin-stl-clr.md)