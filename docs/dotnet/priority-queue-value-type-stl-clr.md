---
title: "priority_queue:: value_type (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::priority_queue::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 0d81ef75-8bd1-44f5-8753-4b42a505d8c3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 494b9882789057809fd5857a810bd6991344067e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueuevaluetype-stlclr"></a>priority_queue::value_type (STL/CLR)
元素的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>備註  
 此類型是範本參數 `Value`的同義字。  
  
## <a name="example"></a>範例  
  
```  
// cliext_priority_queue_value_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mypriority_queue::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority_queue::reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)