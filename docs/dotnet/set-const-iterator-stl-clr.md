---
title: "set::const_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::const_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_iterator 成員 [STL/CLR]"
ms.assetid: de234ad4-d420-4da8-a13a-1aec8c337d8b
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::const_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於受控制序列的常數迭代器類型。  
  
## 語法  
  
```  
typedef T2 const_iterator;  
```  
  
## 備註  
 型別描述可以當做常數雙向 Iterator 為此控制序列未指定型別 `T2` 的物件。  
  
## 範例  
  
```  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標題:** \<cliext\/設定\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::iterator](../dotnet/set-iterator-stl-clr.md)