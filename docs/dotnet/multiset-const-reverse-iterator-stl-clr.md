---
title: "multiset::const_reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator 成員 [STL/CLR]"
ms.assetid: f345ddd5-c871-4a6c-a6a4-b90eb843665c
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::const_reverse_iterator (STL/CLR)
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
// cliext_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Mymultiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b。**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::reverse\_iterator](../dotnet/multiset-reverse-iterator-stl-clr.md)