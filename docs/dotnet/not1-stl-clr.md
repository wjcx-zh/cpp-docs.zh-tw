---
title: "not1 (STL/CLR) | Microsoft Docs"
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
  - "cliext::not1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not1 函式 [STL/CLR]"
ms.assetid: a50cd819-10de-4d81-84da-8a34c5414a43
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# not1 (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生函子的 `unary_negate` 。  
  
## 語法  
  
```  
template<typename Fun>  
    unary_negate<Fun> not1(Fun% functor);  
```  
  
## Template Parameters  
 Fun  
 功能子的型別。  
  
## 函式參數  
 功能子  
 要包裝的功能子。  
  
## 備註  
 樣板函式會傳回 [unary\_negate](../dotnet/unary-negate-stl-clr.md)`<``Fun``>(functor)`。  您將它當做一個包裝表示邏輯 NOT 的單引數函子至函數中的便利功能。  
  
## 範例  
  
```  
// cliext_not1.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 0**  
 **1 0**  
 **1 0**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [unary\_negate](../dotnet/unary-negate-stl-clr.md)