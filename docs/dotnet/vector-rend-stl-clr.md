---
title: 'vector:: rend (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::rend
dev_langs:
- C++
helpviewer_keywords:
- rend member [STL/CLR]
ms.assetid: 8dc1927f-9214-468d-877e-eda20c03e90d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 36d701d9259720663b12a0d2985ff2a97f16940b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="vectorrend-stlclr"></a>vector::rend (STL/CLR)
指定反向受控制序列的結尾。  
  
## <a name="syntax"></a>語法  
  
```  
reverse_iterator rend();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回以外的位置開始，指向受控制序列的反向迭代器。 因此，它會指定`end`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更結尾受控制的序列相反的順序出現，但它的狀態。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)   
 [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md)   
 [vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)