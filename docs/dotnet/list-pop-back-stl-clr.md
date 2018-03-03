---
title: "list:: pop_back (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::list::pop_back
dev_langs:
- C++
helpviewer_keywords:
- pop_back member [STL/CLR]
ms.assetid: 03fe8e0e-461b-41c4-8e20-97d0d4ed0feb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e6794af1a04a9e5fdf756de6470eed6e62bbb0c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="listpopback-stlclr"></a>list::pop_back (STL/CLR)
移除最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
void pop_back();  
```  
  
## <a name="remarks"></a>備註  
 成員函式中移除受控制的序列必須為非空白的最後一個元素。 您可以使用它來縮短在最後一個項目清單。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)   
 [list:: push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)   
 [list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)