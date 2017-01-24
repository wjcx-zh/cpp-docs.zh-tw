---
title: "not2 (STL/CLR) | Microsoft Docs"
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
  - "cliext::not2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not2 函式 [STL/CLR]"
ms.assetid: f8aedcca-e4d1-4430-93b4-83dd55579d04
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# not2 (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生工具功能的 `binary_negate` 。  
  
## 語法  
  
```  
template<typename Fun>  
    binary_negate<Fun> not2(Fun% functor);  
```  
  
## Template Parameters  
 有趣。  
 功能的類型。  
  
## 函式參數  
 功能。  
 包裝的功能\)。  
  
## 備註  
 樣板函式會傳回 [binary\_negate](../dotnet/binary-negate-stl-clr.md)`<``Fun``>(functor)`。  您將它當做一個便利包裝在傳遞其邏輯 NOT 功能中的一或兩個引數的功能。  
  
## 範例  
  
```  
// cliext_not2.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **4 4**  
 **1 0**  
 **1 0**   
## 需求  
 **標題:** \<cliext\/功能\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [binary\_negate](../dotnet/binary-negate-stl-clr.md)