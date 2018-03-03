---
title: "queue:: front (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::queue::front
dev_langs:
- C++
helpviewer_keywords:
- front member [STL/CLR]
ms.assetid: 9d7bb95f-5896-42f7-86fa-004a7a65cc94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4726377c30300ee1a139b2a596346ea5cdc804f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="queuefront-stlclr"></a>queue::front (STL/CLR)
存取第一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
reference front();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列必須為非空白的第一個元素的參考。 您可以使用它來存取第一個項目中，當您知道它存在。  
  
## <a name="example"></a>範例  
  
```  
// cliext_queue_front.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue:: back (STL/CLR)](../dotnet/queue-back-stl-clr.md)   
 [queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)   
 [queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)