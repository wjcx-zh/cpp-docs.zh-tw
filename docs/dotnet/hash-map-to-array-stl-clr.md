---
title: hash_map::to_array (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::to_array
dev_langs:
- C++
helpviewer_keywords:
- to_array member [STL/CLR]
ms.assetid: 26d7620f-893b-47f2-99e3-f0b6af3aedc9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76e6d4c11473fd78a8dcb41afb4c7726f70afe15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106163"
---
# <a name="hashmaptoarray-stlclr"></a>hash_map::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列的陣列。 您可以使用它來取得陣列的形式受控制序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_map_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Myhash_map::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Myhash_map::make_value(L'd', 4));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Myhash_map::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)