---
title: "multimap::const_reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator 成員 [STL/CLR]"
ms.assetid: edc5129e-f2ca-4d3a-a898-365ad0a587e4
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::const_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常數反向 Iterator 的型別受控制序列中。  
  
## 語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## 備註  
 型別描述可以當做常數反向 Iterator 為此控制序列未指定型別 `T4` 的物件。  
  
## 範例  
  
```  
// cliext_multimap_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Mymultimap::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[c 3\] \[2\] \[b 以 1\]**   
## 需求  
 **標題:** \<cliext\/對應\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::reverse\_iterator](../dotnet/multimap-reverse-iterator-stl-clr.md)