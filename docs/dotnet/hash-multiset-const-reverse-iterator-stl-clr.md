---
title: "hash_multiset:: const_reverse_iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::const_reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_reverse_iterator member [STL/CLR]
ms.assetid: 55214d17-94c3-4517-8996-ae28ff37225b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 07dff1022debfa6dcb11d542528bd1e1ff850952
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetconstreverseiterator-stlclr"></a>hash_multiset::const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器型別...  
  
## <a name="syntax"></a>語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::reverse_iterator (STL/CLR)](../dotnet/hash-multiset-reverse-iterator-stl-clr.md)