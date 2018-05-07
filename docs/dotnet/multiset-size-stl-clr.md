---
title: 'multiset:: size (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::size
dev_langs:
- C++
helpviewer_keywords:
- size member [STL/CLR]
ms.assetid: 29338f4f-c13e-4eb6-844d-1d94769553c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 29b30aeeb5fe515604c7cd172123a2b8effcdbf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multisetsize-stlclr"></a>multiset::size (STL/CLR)
計算元素的數目。  
  
## <a name="syntax"></a>語法  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的項目數。 如果您在意順序是否具有非零的大小，請參閱[multiset:: empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)`()`。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_size.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)