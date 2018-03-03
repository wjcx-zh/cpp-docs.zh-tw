---
title: "priority_queue:: priority_queue (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::priority_queue::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue member [STL/CLR]
ms.assetid: aab423d7-959e-48fd-9028-e9f45f43cb8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03d0054f3c755c3dd6e4bd653c972a0f7aa6735d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueuepriorityqueue-stlclr"></a>priority_queue::priority_queue (STL/CLR)
建構容器配接器物件。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 接續  
 要複製的容器。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 pred  
 排序受控制序列的述詞。  
  
 向右  
 要插入的物件或範圍。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `priority_queue();`  
  
 建立空的已包裝的容器，使用預設排序述詞。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞。  
  
 建構函式：  
  
 `priority_queue(priority_queue<Value, Container>% right);`  
  
 建立複本的已包裝的容器`right.get_container()`，順序的述詞`right.value_comp()`。 您用它來指定佇列物件所控制之序列的複本初始受控制的序列`right`，具有相同順序的述詞。  
  
 建構函式：  
  
 `priority_queue(priority_queue<Value, Container>^ right);`  
  
 建立複本的已包裝的容器`right->get_container()`，順序的述詞`right->value_comp()`。 您用它來指定佇列物件所控制之序列的複本初始受控制的序列`*right`，具有相同順序的述詞。  
  
 建構函式：  
  
 `explicit priority_queue(value_compare^ pred);`  
  
 順序的述詞建立一個空的已包裝的容器`pred`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞。  
  
 建構函式：  
  
 `priority_queue(value_compare^ pred, container_type cont);`  
  
 順序的述詞建立一個空的已包裝的容器`pred`，接著會將所有項目`cont`您用它來指定受控制的初始序列，從現有的容器，以指定順序的述詞。  
  
 建構函式：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last);`  
  
 使用預設排序述詞，建立空的已包裝的容器，然後推入序列 [`first`， `last`)。 您可以使用它來指定順序的述詞指定從指定的 eqeuence，初始受控制的序列。  
  
 建構函式：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred);`  
  
 順序的述詞建立一個空的已包裝的容器`pred`，接著會將序列 [`first`， `last`)。 您可以使用它來指定順序的述詞指定從指定的 seqeuence，初始受控制的序列。  
  
 建構函式：  
  
 `template<typename InIt> priority_queue(InIt first, InIt last, value_compare^ pred, container_type% cont);`  
  
 順序的述詞建立一個空的已包裝的容器`pred`，接著會將所有項目`cont`再加上順序 [`first`， `last`)。 您可以使用它來指定順序的述詞指定從現有的容器和指定的 seqeuence，初始受控制的序列。  
  
## <a name="example"></a>範例  
  
```cpp  
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
  
```Output  
size() = 0  
 c a b  
size() = 0  
 a c b  
 a c b  
 c a b  
 a c b  
 a a b c c b  
 c a b  
 c a b  
 a c b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)   
 [priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)   
 [priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)