---
title: "queue:: queue (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::queue::queue
dev_langs: C++
helpviewer_keywords: queue member [STL/CLR]
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6c4b24ad40bf19b7a20aafcfa2d02fb6490fed1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="queuequeue-stlclr"></a>queue::queue (STL/CLR)
建構容器配接器物件。  
  
## <a name="syntax"></a>語法  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製的物件。  
  
 換行  
 已包裝的容器使用。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `queue();`  
  
 建立空的已包裝的容器。 您可以用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `queue(queue<Value, Container>% right);`  
  
 建立複本的已包裝的容器`right.get_container()`。 您用它來指定佇列物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `queue(queue<Value, Container>^ right);`  
  
 建立複本的已包裝的容器`right->get_container()`。 您用它來指定佇列物件所控制之序列的複本初始受控制的序列`*right`。  
  
 建構函式：  
  
 `explicit queue(container_type wrapped);`  
  
 使用現有的容器`wrapped`做為包裝的容器。 您可以使用它來建構從現有容器的佇列。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)   
 [queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)