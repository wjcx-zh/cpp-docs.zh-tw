---
title: "stack::stack (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stack 成員 [STL/CLR]"
ms.assetid: f1cfb3fe-4d22-41e5-906b-e8faa0bcde9b
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構容器配接器物件。  
  
## 語法  
  
```  
stack();  
stack(stack<Value, Container>% right);  
stack(stack<Value, Container>^ right);  
explicit stack(container_type% wrapped);  
```  
  
#### 參數  
 right  
 要複製的物件。  
  
 包裝  
 使用的包裝的容器。  
  
## 備註  
 建構函式:  
  
 `stack();`  
  
 建立空包裝的容器。  您會用它來指定一個空的初始控制順序。  
  
 建構函式:  
  
 `stack(stack<Value, Container>% right);`  
  
 為 `right.get_container()`建立複本的包裝的容器。  您會用它來指定要複製順序由堆疊物件 `right`的初始控制順序。  
  
 建構函式:  
  
 `stack(stack<Value, Container>^ right);`  
  
 為 `right->get_container()`建立複本的包裝的容器。  您會用它來指定要複製順序由堆疊物件 `*right`的初始控制順序。  
  
 建構函式:  
  
 `explicit stack(container_type% wrapped);`  
  
 使用現有的容器 `wrapped` 做為包裝的容器。  用來從現有的容器的堆疊。  
  
## 範例  
  
```  
// cliext_stack_construct.cpp   
// compile with: /clr   
#include <cliext/stack>   
#include <cliext/vector>   
  
typedef cliext::stack<wchar_t> Mystack;   
typedef cliext::vector<wchar_t> Myvector;   
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;   
int main()   
    {   
// construct an empty container   
    Mystack c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Myvector v2(5, L'x');   
    Mystack_vec c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mystack_vec c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Mystack_vec c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **大小 \(\) \= 0**  
 **x x x x x**  
 **x x x x x**  
 **x x x x x**   
## 需求  
 **標題:** \<cliext\/堆疊\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [堆疊](../dotnet/stack-stl-clr.md)   
 [stack::assign](../dotnet/stack-assign-stl-clr.md)   
 [stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)   
 [stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)