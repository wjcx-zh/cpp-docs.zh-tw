---
title: "multiset:: const_iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::const_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_iterator member [STL/CLR]
ms.assetid: 42855717-f118-4315-95b0-763f94bba888
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a0de4d2bbc90f739913a9182edd0d14fe363562d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multisetconstiterator-stlclr"></a>multiset::const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T2`，可做為受控制序列的常數的雙向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_const_iterator.cpp   
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
    Mymultiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
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
 [multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)