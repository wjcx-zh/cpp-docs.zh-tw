---
title: 'priority_queue:: push (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue::push
dev_langs:
- C++
helpviewer_keywords:
- push member [STL/CLR]
ms.assetid: 317d3feb-0688-4658-866b-a26cae060354
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7402af9a18f3d0f2f9f434393f5645d4267bb5b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueuepush-stlclr"></a>priority_queue::push (STL/CLR)
加入新項目。  
  
## <a name="syntax"></a>語法  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>備註  
 成員函式插入值的項目`val`到受控制的序列，並重新排列維護堆積專業領域的受控制的序列。 您可以使用它來將另一個項目加入佇列。  
  
## <a name="example"></a>範例  
  
```  
// cliext_priority_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::pop (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)