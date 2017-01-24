---
title: "multiset::const_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::const_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_iterator 成員 [STL/CLR]"
ms.assetid: 42855717-f118-4315-95b0-763f94bba888
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::const_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於受控制序列的常數迭代器類型。  
  
## 語法  
  
```  
typedef T2 const_iterator;  
```  
  
## 備註  
 此型別描述未指定型別 `T2` 的物件，其可以在控制序列中作為常數隨機讀取迭代器。  
  
## 範例  
  
```  
// cliext_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Mymultiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::iterator](../dotnet/multiset-iterator-stl-clr.md)