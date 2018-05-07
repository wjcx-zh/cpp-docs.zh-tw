---
title: 'hash_multimap:: value_type (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: f15cbeb0-bd65-4299-93a1-4fe151d7452e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c94ec00d4dd5b83c5e9929f9c339a431caed291
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultimapvaluetype-stlclr"></a>hash_multimap::value_type (STL/CLR)
元素的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>備註  
 這個類型與 `generic_value`同義。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multimap_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Myhash_multimap::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_multimap::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap:: const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)   
 [hash_multimap:: key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)   
 [hash_multimap::reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)