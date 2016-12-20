---
title: "operator&lt;= (stack) (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator<= 成員 [STL/CLR]"
ms.assetid: fd2f500b-84d1-4eed-98ba-3a6f481ae8f5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt;= (stack) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

堆疊小於或等於比較。  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的正確的容器。  
  
## 備註  
 運算子函式會傳回 `!(``right``<``left``)`。  您會用它來測試 `left` 沒有在 `right` 之後已排序，當兩個堆疊是比較項目由項目時。  
  
## 範例  
  
```  
// cliext_stack_operator_le.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
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
 **標題:** \<cliext\/堆疊\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [operator\=\= \(stack\)](../dotnet/operator-equality-stack-stl-clr.md)   
 [operator\!\= \(stack\)](../dotnet/operator-inequality-stack-stl-clr.md)   
 [operator\< \(stack\)](../dotnet/operator-less-than-stack-stl-clr.md)   
 [operator\>\= \(stack\)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)   
 [operator\> \(stack\)](../dotnet/operator-greater-than-stack-stl-clr.md)