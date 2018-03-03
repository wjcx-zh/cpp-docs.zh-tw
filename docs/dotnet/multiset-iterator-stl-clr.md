---
title: "multiset:: iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::iterator
dev_langs:
- C++
helpviewer_keywords:
- iterator member [STL/CLR]
ms.assetid: 0e8fff2a-f90e-4ba6-816a-5a2dc77c51e3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 087b92a5776706d168abf7412f4ed6014fbb67e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multisetiterator-stlclr"></a>multiset::iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T1`，可做為受控制序列的雙向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Mymultiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)