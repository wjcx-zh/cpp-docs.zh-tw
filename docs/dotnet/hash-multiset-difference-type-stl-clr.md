---
title: 'hash_multiset:: difference_type (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::difference_type
dev_langs:
- C++
helpviewer_keywords:
- difference_type member [STL/CLR]
ms.assetid: 31e492b1-e980-4799-bab2-0dd2864428c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ccc34f218b2352132df9c90092a044abfe6c5873
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultisetdifferencetype-stlclr"></a>hash_multiset::difference_type (STL/CLR)
兩個項目之間的帶正負號距離的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef int difference_type;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述負可能是項目計數。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multiset_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::difference_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::size_type (STL/CLR)](../dotnet/hash-multiset-size-type-stl-clr.md)