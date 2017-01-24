---
title: "operator= (deque) (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 成員 [STL/CLR]"
ms.assetid: 0851c6e2-29a2-45da-8c5a-e0b2f5357fb6
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator= (deque) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取代受控制序列。  
  
## 語法  
  
```  
deque<Value>% operator=(deque<Value>% right);  
```  
  
#### 參數  
 right  
 要複製的容器。  
  
## 備註  
 成員運算子複製 `right` 到物件後，再傳回 `*this`。  您會用它將受控制序列取代為它在 `right`的副本。  
  
## 範例  
  
```  
// cliext_deque_operator_as.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## 需求  
 **標頭：** \<cliext\/deque\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)