---
title: "list::rend (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::rend"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rend 成員 [STL/CLR]"
ms.assetid: b51030ad-1bca-42b0-b890-db47111d2921
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::rend (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定已還原的受控制序列結尾。  
  
## 語法  
  
```  
reverse_iterator rend();  
```  
  
## 備註  
 成員函式傳回在受控制序列的開頭之外按的反向 Iterator。  因此，它會指定反向序列的 `end`。  您要用它來取得的 Iterator 可指定以相反順序顯示的受控制序列之 `current` 結尾，但是，如果受控制序列的長度變更，它的狀態也可以變更。  
  
## 範例  
  
```  
// cliext_list_rend.cpp   
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
  
// inspect first two items   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*\-\- \-\-rend\(\) \= b**  
**\*\-\-盡可能 \(\=\)。**  
 **y x c**   
## 需求  
 **標題:** \<cliext\/清單\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::begin](../dotnet/list-begin-stl-clr.md)   
 [list::end](../dotnet/list-end-stl-clr.md)   
 [list::rbegin](../dotnet/list-rbegin-stl-clr.md)