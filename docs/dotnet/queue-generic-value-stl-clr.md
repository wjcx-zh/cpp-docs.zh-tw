---
title: queue::generic_value (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::generic_value
dev_langs:
- C++
helpviewer_keywords:
- generic_value member [STL/CLR]
ms.assetid: 5efd9812-6b4d-4e59-b8e8-c4975ae61667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: edec05e49b5117a47bdc2aeed59d7dc9a0d2921f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33162455"
---
# <a name="queuegenericvalue-stlclr"></a>queue::generic_value (STL/CLR)
使用容器的泛型介面的項目類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>備註  
 此類型所描述型別的物件`GValue`描述使用的預存的項目值與此範本容器類別的泛型介面。 (`GValue`是`value_type`或`value_type^`如果`value_type`ref 型別。)  
  
## <a name="example"></a>範例  
  
```  
// cliext_queue_generic_value.cpp   
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
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)