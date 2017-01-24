---
title: "operator&gt; (stack) (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator> 成員 [STL/CLR]"
ms.assetid: 77979026-bed5-4d24-a2af-f720f8c362a2
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt; (stack) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

堆疊大於比較。  
  
## 語法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### 參數  
 left  
 要比較的左邊容器。  
  
 right  
 要比較的右邊容器。  
  
## 備註  
 運算子函式會傳回 `right` `<` `left`。  您會用它來測試在兩個堆疊在逐一項目比較後，`left` 是否在 `right` 之後已排序。  
  
## 範例  
  
```  
// cliext_stack_operator_gt.cpp   
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
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b d**  
**\[a b c\] \> \[a b c\] is False**  
**\[a b d\] \> \[a b c\] is True**   
## 需求  
 **標頭：** \<cliext\/stack\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [operator\=\= \(stack\)](../dotnet/operator-equality-stack-stl-clr.md)   
 [operator\!\= \(stack\)](../dotnet/operator-inequality-stack-stl-clr.md)   
 [operator\< \(stack\)](../dotnet/operator-less-than-stack-stl-clr.md)   
 [operator\>\= \(stack\)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)   
 [operator\<\= \(stack\)](../dotnet/operator-less-or-equal-stack-stl-clr.md)