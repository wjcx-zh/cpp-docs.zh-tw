---
title: "operator&gt;= (queue) (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator>= 成員 [STL/CLR]"
ms.assetid: 55504da4-90a9-4c02-94df-10ba51b6b7cc
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt;= (queue) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

佇列「大於或等於」的比較。  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>=(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 運算子函式會傳回 `!(``left` `<` `right``)`。  您可用它來測試當這兩個佇列逐一比較項目時， `left` 是否在 `right` 排序之前。  
  
## 範例  
  
```  
// cliext_queue_operator_ge.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \>\= \[a b c\] is True**  
**\[a b c\] \>\= \[a b d\] is False**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)   
 [operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator\< \(queue\)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [operator\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)