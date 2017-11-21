---
title: "deque:: back (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::back
dev_langs: C++
helpviewer_keywords: back member [STL/CLR]
ms.assetid: 5608cdda-212d-42f6-866b-b04aec04ef8e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d262b25279cd9fcd330779a42161acd1881188e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="dequeback-stlclr"></a>deque::back (STL/CLR)
存取最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
reference back();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列必須為非空白的最後一個元素的參考。 您可以使用它來存取最後一個項目中，當您知道它存在。  
  
## <a name="example"></a>範例  
  
```  
// cliext_deque_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)   
 [deque:: front (STL/CLR)](../dotnet/deque-front-stl-clr.md)   
 [deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)