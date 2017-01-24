---
title: "list::reverse_iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator 成員 [STL/CLR]"
ms.assetid: 56853ed8-cb12-41d7-98b2-c511cd77945d
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於受控制序列的反向迭代器型別。  
  
## 語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## 備註  
 此型別描述其可以為此控制序列當做反向迭代器之未指定型別 `T3` 的物件。  
  
## 範例  
  
```  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c b a**  
 **x b a**   
## 需求  
 **標頭 ：** \<cliext\/list\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [list](../dotnet/list-stl-clr.md)   
 [list::const\_iterator](../dotnet/list-const-iterator-stl-clr.md)   
 [list::const\_reverse\_iterator](../dotnet/list-const-reverse-iterator-stl-clr.md)   
 [list::iterator](../dotnet/list-iterator-stl-clr.md)