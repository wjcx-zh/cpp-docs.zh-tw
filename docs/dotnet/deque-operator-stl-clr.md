---
title: "deque::operator(STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator[] 成員 [STL/CLR]"
ms.assetid: d7653bb5-db48-4637-a25c-e7303e5d28da
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::operator(STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取項目在指定的位置。  
  
## 語法  
  
```  
reference operator[](size_type pos);  
```  
  
#### 參數  
 pos  
 要存取之項目的位置。  
  
## 備註  
 成員運算子傳回 referene 對這個項目位於 `pos`。  您會用它來存取位置您辨識的項目。  
  
## 範例  
  
```  
// cliext_deque_operator_sub.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **x c**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::at](../dotnet/deque-at-stl-clr.md)