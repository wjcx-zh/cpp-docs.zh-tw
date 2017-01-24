---
title: "operator&lt;= (deque) (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator<= 成員 [STL/CLR]"
ms.assetid: b70cc499-35fb-4fa5-b8e3-5270bc647ace
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt;= (deque) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

雙向佇列小於或等於比較。  
  
## 語法  
  
```  
template<typename Value>  
    bool operator<=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的正確的容器。  
  
## 備註  
 運算子函式會傳回 `!(``right``<``left``)`。  您會用它來測試 `left` 沒有在 `right` 之後已排序，當兩個雙佇列是比較項目由項目時。  
  
## 範例  
  
```  
// cliext_deque_operator_le.cpp   
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
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **b d**  
**\[b c\] \<\[\= b c\] 為 true**  
**\[b d \[\] \<\= b c\] 為 false**   
## 需求  
 **標題:** \<cliext\/雙向佇列\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [deque](../dotnet/deque-stl-clr.md)   
 [operator\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)   
 [deque::operator\!\=](../dotnet/deque-operator-inequality-stl-clr.md)   
 [operator\< \(deque\)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [operator\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [operator\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)