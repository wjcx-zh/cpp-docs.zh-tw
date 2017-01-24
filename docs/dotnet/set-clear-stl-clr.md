---
title: "set::clear (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear 成員 [STL/CLR]"
ms.assetid: 52b39d7d-d479-45ff-a652-61cd26eb0c9b
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除所有項目。  
  
## 語法  
  
```  
void clear();  
```  
  
## 備註  
 成員函式有效地呼叫 [set::erase](../dotnet/set-erase-stl-clr.md)`(` [set::begin](../dotnet/set-begin-stl-clr.md)`(),` [set::end](../dotnet/set-end-stl-clr.md)`())`。  您會用它來確保受控制序列是空的。  
  
## 範例  
  
```  
// cliext_set_clear.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 0**  
 **a b**  
**size\(\) \= 0**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)   
 [set::erase](../dotnet/set-erase-stl-clr.md)