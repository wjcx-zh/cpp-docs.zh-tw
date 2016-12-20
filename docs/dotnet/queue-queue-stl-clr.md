---
title: "queue::queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queue 成員 [STL/CLR]"
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構容器配接器物件。  
  
## 語法  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### 參數  
 right  
 要複製的物件。  
  
 包裝  
 使用的包裝容器。  
  
## 備註  
 建構函式：  
  
 `queue();`  
  
 建立空包裝的容器。  您會用它來指定一個空的初始控制順序。  
  
 建構函式:  
  
 `queue(queue<Value, Container>% right);`  
  
 為 `right.get_container()`建立複本的包裝容器。  您會用它來指定要複製順序以佇列物件 `right`的初始控制順序。  
  
 建構函式:  
  
 `queue(queue<Value, Container>^ right);`  
  
 為 `right->get_container()`建立複本的包裝容器。  您會用它來指定要複製順序以佇列物件 `*right`的初始控制順序。  
  
 建構函式:  
  
 `explicit queue(container_type wrapped);`  
  
 使用現有的容器 `wrapped` 做為包裝的容器。  用它來從現有的容器建立佇列。  
  
## 範例  
  
```  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **x x x x x**  
 **x x x x x**  
 **x x x x x**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::assign](../dotnet/queue-assign-stl-clr.md)   
 [queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)