---
title: hash_map::make_value (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::make_value
dev_langs:
- C++
helpviewer_keywords:
- make_value member [STL/CLR]
ms.assetid: 1fcdcacc-5edf-46b7-9481-9a4aef32b025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9592a147daf119dd8f8dc1fd9c70d128276784d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmapmakevalue-stlclr"></a>hash_map::make_value (STL/CLR)
建構值物件。  
  
## <a name="syntax"></a>語法  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 若要使用的金鑰值。  
  
 對應  
 要搜尋的對應的值。  
  
## <a name="remarks"></a>備註  
 成員函式傳回`value_type`物件的索引鍵是`key`、 其對應的值為`mapped`。 您可以使用它來撰寫適用於數個其他成員函式物件。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_map_make_value.cpp   
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
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: key_type (STL/CLR)](../dotnet/hash-map-key-type-stl-clr.md)   
 [hash_map:: mapped_type (STL/CLR)](../dotnet/hash-map-mapped-type-stl-clr.md)   
 [hash_map::value_type (STL/CLR)](../dotnet/hash-map-value-type-stl-clr.md)