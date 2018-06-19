---
title: 'list:: const_reference (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::const_reference
dev_langs:
- C++
helpviewer_keywords:
- const_reference member [STL/CLR]
ms.assetid: bd8f6411-b8e4-4597-abd5-c0eabdf36f64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 272da48bbbf4c968a050c645962b481aa9a2130e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129407"
---
# <a name="listconstreference-stlclr"></a>list::const_reference (STL/CLR)
項目的常數參考類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef value_type% const_reference;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述項目的常數參考。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_const_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::list<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)   
 [list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)