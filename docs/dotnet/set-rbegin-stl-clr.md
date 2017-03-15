---
title: "set::rbegin (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::rbegin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rbegin 成員 [STL/CLR]"
ms.assetid: b9da72dc-0b75-489e-b179-74c27a4bcfb7
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::rbegin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定已還原的受控制序列開頭。  
  
## 語法  
  
```  
reverse_iterator rbegin();  
```  
  
## 備註  
 成員函式來傳回指定受控制序列的最後一個項目在空序列開頭的之外的反向 Iterator，則為。  因此，它會指定反向序列的 `beginning`。  您會用它來取得指定以反向順序顯示之受控制序列 `current` 開頭的 Iterator，但是如果受控制序列的長度變更，它的狀態也會變更。  
  
## 範例  
  
```  
// cliext_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*rbegin \(\) \= c**  
**\*\+\+rbegin \(\) \= b**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::begin](../dotnet/set-begin-stl-clr.md)   
 [set::end](../dotnet/set-end-stl-clr.md)   
 [set::rend](../dotnet/set-rend-stl-clr.md)