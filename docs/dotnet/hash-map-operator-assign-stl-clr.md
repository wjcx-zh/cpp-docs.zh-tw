---
title: 'hash_map:: operator = (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: fbcbae4c-c8f8-431e-831b-a40cce00a88c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5deef602bbbab5c24406a67f67478fb900d4e106
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmapoperator-stlclr"></a>hash_map::operator= (STL/CLR)
取代受控制的序列。  
  
## <a name="syntax"></a>語法  
  
```  
hash_map<Key, Mapped>% operator=(hash_map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製的容器。  
  
## <a name="remarks"></a>備註  
 成員運算子複製`right`物件，然後傳回`*this`。 您使用它將受控制序列取代為 `right` 中受控制序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_map_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_map c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)