---
title: "set::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成員 [STL/CLR]"
ms.assetid: 14e16799-d188-4e0d-a0ce-be2c98f93cc8
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取代受控制序列。  
  
## 語法  
  
```  
set<Key>% operator=(set<Key>% right);  
```  
  
#### 參數  
 right  
 要複製的容器。  
  
## 備註  
 成員運算子複製 `right` 到物件後，再傳回 `*this`。  您會用它將受控制序列取代為它在 `right`的副本。  
  
## 範例  
  
```  
// cliext_set_operator_as.cpp   
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
    for each (Myset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/set\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [set](../dotnet/set-stl-clr.md)