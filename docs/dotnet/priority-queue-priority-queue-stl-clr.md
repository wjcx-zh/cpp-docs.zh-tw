---
title: "priority_queue::priority_queue (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "priority_queue 成員 [STL/CLR]"
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::priority_queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構容器配接器物件。  
  
## 語法  
  
```  
priority_queue();  
priority_queue(priority_queue<Value, Container> right);  
priority_queue(priority_queue<Value, Container> right);  
explicit priority_queue(value_compare^ pred);  
priority_queue(value_compare^ pred, container_type% cont);  
template<typename InIt>  
    priority_queue(InIt first, InIt last);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred);  
template<typename InIt>  
    priority_queue(InIt first, InIt last,  
        value_compare^ pred, container_type% cont);  
```  
  
#### 參數  
 cont  
 要複製的容器。  
  
 first  
 要插入的範圍開頭。  
  
 last  
 要插入的範圍結尾。  
  
 pred  
 為控制序列預先定義的述詞。  
  
 right  
 要插入的物件或範圍 。  
  
## 備註  
 建構函式:  
  
 `priority_queue();`  
  
 建立空的已包裝容器，以及預設定序的述詞。  您會用它來指定一個空的初始控制序列，與預設定序述詞。  
  
 建構函式:  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 建立為 `right.get_container()`複本的包裝容器，以及有定序述詞的 `right.value_comp()`。  您會用它來指定為由多重集物件 `right`控制的多重集合的拷貝的相同控制序列，以及預設定序述詞。  
  
 建構函式:  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 建立為 `right->get_container()`複本的包裝容器，以及有定序述詞的 `right->value_comp()`。  您會用它來指定為由多重集物件 `*right`控制的多重集合的拷貝的相同控制序列，以及預設定序述詞。  
  
 建構函式:  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 建立空的已包裝容器，以及序述詞  `pred`。  您會用它來指定一個空的初始控制序列，與指定序述詞。  
  
 建構函式:  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 建立空的包裝容器，有定序述詞的 `pred`，然後推進 `cont` 的所有項目。您用來指定從現有的容器的初始控制序列 ，以及指定的順序述詞。  
  
 建構函式:  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last);`  
  
 建立空的包裝容器，以及預設定序述詞，然後推進序列 `[``first``,` `last``)`。  您會用它來指定從指定的序列的初始控制序列，以及指定的順序述詞。  
  
 建構函式:  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last,`  
  
 `value_compare^ pred);`  
  
 建立空的包裝容器，以及定序述詞 `pred`，然後推進序列 `[``first``,` `last``)`。  您會用它來指定從指定的序列的初始控制序列，以及指定的順序述詞。  
  
 建構函式:  
  
 `template<typename InIt>`  
  
 `priority_queue(InIt first, InIt last,`  
  
 `value_compare^ pred, container_type% cont);`  
  
 建立空的包裝容器，以及定序述詞 `pred`，然後推進 `cont` 的所有元素加上序列 `[``first``,` `last``)`。  您會用它來指定從現有的容器和指定的序列的初始控制序列，以及指定的順序述詞。  
  
## 範例  
  
```  
// cliext_priority_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/deque>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
typedef cliext::deque<wchar_t> Mydeque;   
int main()   
    {   
// construct an empty container   
    Mypriority_queue c1;   
    Mypriority_queue::container_type^ wc1 = c1.get_container();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    for each (wchar_t elem in wc1)   
        c2.push(elem);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule by copying an underlying container   
    Mypriority_queue c2x =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
   for each (wchar_t elem in c2x.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mypriority_queue c3(wc1->begin(), wc1->end());   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mypriority_queue c4(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>());   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range, another container, and an ordering rule   
    Mypriority_queue c5(wc1->begin(), wc1->end(),   
        cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c5.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Mypriority_queue c6(c3);   
    for each (wchar_t elem in c6.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mypriority_queue c7(%c3);   
    for each (wchar_t elem in c7.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule, by copying an underlying container   
    Mypriority_queue c8 =   
        gcnew Mypriority_queue(cliext::greater<wchar_t>(), *wc1);   
    for each (wchar_t elem in c8.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **c a b**  
**size\(\) \= 0**  
 **a c b**  
 **a c b**  
 **c a b**  
 **a c b**  
 **a a b c c b**  
 **c a b**  
 **c a b**  
 **a c b**   
## 需求  
 **標頭：** \<cliext\/queue\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::assign](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority\_queue::generic\_container](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)