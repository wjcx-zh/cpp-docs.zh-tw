---
title: 'hash_multiset:: rend (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::rend
dev_langs:
- C++
helpviewer_keywords:
- rend member [STL/CLR]
ms.assetid: 6d007ac9-18cc-4b51-8384-a4ff65d23e97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d75d8fc85a6a1cde37e8c9cf7edc93acd55a5c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultisetrend-stlclr"></a>hash_multiset::rend (STL/CLR)
指定反向受控制序列的結尾。  
  
## <a name="syntax"></a>語法  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回以外的位置開始，指向受控制序列的反向迭代器。 因此，它會指定`end`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更結尾受控制的序列相反的順序出現，但它的狀態。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multiset_rend.cpp   
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
  
// inspect first two items   
    Myhash_multiset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset:: begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md)   
 [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)   
 [hash_multiset::rbegin (STL/CLR)](../dotnet/hash-multiset-rbegin-stl-clr.md)