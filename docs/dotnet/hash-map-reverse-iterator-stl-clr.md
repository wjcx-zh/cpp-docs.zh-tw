---
title: 'hash_map:: reverse_iterator (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- reverse_iterator member [STL/CLR]
ms.assetid: 63778922-82e5-4692-8447-da8964a974bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c0b5e6d0ff90b11e44ff6e990cc69b5832eb2ab5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmapreverseiterator-stlclr"></a>hash_map::reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: const_iterator (STL/CLR)](../dotnet/hash-map-const-iterator-stl-clr.md)   
 [hash_map:: const_reverse_iterator (STL/CLR)](../dotnet/hash-map-const-reverse-iterator-stl-clr.md)   
 [hash_map::iterator (STL/CLR)](../dotnet/hash-map-iterator-stl-clr.md)