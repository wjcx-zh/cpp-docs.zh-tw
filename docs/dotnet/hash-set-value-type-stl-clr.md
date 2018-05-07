---
title: 'hash_set:: value_type (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: a83724eb-496a-43ef-b969-b441f258e3be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aa4b690265370c40402f85636de3033db80ea431
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashsetvaluetype-stlclr"></a>hash_set::value_type (STL/CLR)
元素的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>備註  
 這個類型與 `generic_value`同義。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_set_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_set::value_type val = *it;   
  
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
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set:: const_reference (STL/CLR)](../dotnet/hash-set-const-reference-stl-clr.md)   
 [hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)   
 [hash_set::reference (STL/CLR)](../dotnet/hash-set-reference-stl-clr.md)