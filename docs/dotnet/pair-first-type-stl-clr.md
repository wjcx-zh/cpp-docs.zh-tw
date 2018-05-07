---
title: pair::first_type (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::pair::first_type
dev_langs:
- C++
helpviewer_keywords:
- first_type member [STL/CLR]
ms.assetid: 8a7792ee-a2f6-4e17-9d0b-9c78007202d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0d7646559255461747b97219c2a15c88e62f5fe4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="pairfirsttype-stlclr"></a>pair::first_type (STL/CLR)
第一個包裝的值類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef Value1 first_type;  
```  
  
## <a name="remarks"></a>備註  
 此類型是範本參數 `Value1`的同義字。  
  
## <a name="example"></a>範例  
  
```  
// cliext_pair_first_type.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    cliext::pair<wchar_t, int>::first_type first_val = c1.first;   
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;   
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/公用程式 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [配對 (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)   
 [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)   
 [pair::second_type (STL/CLR)](../dotnet/pair-second-type-stl-clr.md)