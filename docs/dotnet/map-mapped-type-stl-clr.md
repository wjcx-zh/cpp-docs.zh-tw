---
title: 'map:: mapped_type (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::mapped_type
dev_langs:
- C++
helpviewer_keywords:
- mapped_type member [STL/CLR]
ms.assetid: 818ee40d-8355-446e-a7b2-eb5bf8cc689d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 549a5b6f31375a9b6ea5cc8f07d93d2c223ff6e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mapmappedtype-stlclr"></a>map::mapped_type (STL/CLR)
與每個索引鍵關聯的對應值類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef Mapped mapped_type;  
```  
  
## <a name="remarks"></a>備註  
 此類型是範本參數 `Mapped`的同義字。  
  
## <a name="example"></a>範例  
  
```  
// cliext_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Mymap::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
1 2 3  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)   
 [map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)