---
title: "vector:: const_reverse_iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::const_reverse_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_reverse_iterator member [STL/CLR]
ms.assetid: 5e0a8597-7da4-4545-8826-446a8ee6412d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 966d0b13a4825d60cc34b1bbc758c97cd77650ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vectorconstreverseiterator-stlclr"></a>vector::const_reverse_iterator (STL/CLR)
受控制序列的常數反向迭代器型別...  
  
## <a name="syntax"></a>語法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T4`，可做為受控制序列的常數反向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)