---
title: hash_map::value_compare (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare member [STL/CLR]
ms.assetid: a137d23f-0dd0-4858-ad5e-74782d85bf59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1f6fb402242e6adb8f3a51917e6464f247d55c32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmapvaluecompare-stlclr"></a>hash_map::value_compare (STL/CLR)
兩個項目值順序的委派。  
  
## <a name="syntax"></a>語法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
## <a name="remarks"></a>備註  
 類型是委派，其值的引數的順序會決定的同義字。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'b', 2),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = True  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: key_compare (STL/CLR)](../dotnet/hash-map-key-compare-stl-clr.md)   
 [hash_map:: value_comp (STL/CLR)](../dotnet/hash-map-value-comp-stl-clr.md)   
 [hash_map::value_type (STL/CLR)](../dotnet/hash-map-value-type-stl-clr.md)