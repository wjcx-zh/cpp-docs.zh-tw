---
title: "deque:: value_type (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::value_type
dev_langs: C++
helpviewer_keywords: value_type member [STL/CLR]
ms.assetid: c48528c2-966c-4396-be3c-3b9054689dde
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4ee748e5963cb6adf2f9ef012e8b22e261c3871c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dequevaluetype-stlclr"></a>deque::value_type (STL/CLR)
元素的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef Value value_type;  
```  
  
## <a name="remarks"></a>備註  
 此類型是範本參數 `Value`的同義字。  
  
## <a name="example"></a>範例  
  
```  
// cliext_deque_value_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::deque<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::deque<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)   
 [deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)