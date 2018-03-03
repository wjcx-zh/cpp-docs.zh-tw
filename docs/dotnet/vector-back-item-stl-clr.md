---
title: "vector::back_item (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::back_item
dev_langs:
- C++
helpviewer_keywords:
- back_item member [STL/CLR]
ms.assetid: 9658ffa8-7bde-4242-9ed9-ca42be0d1433
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d8ceeeb1bd339da8cf4bad97117dbcb223206b9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vectorbackitem-stlclr"></a>vector::back_item (STL/CLR)
存取最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
property value_type back_item;  
```  
  
## <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的最後一個元素。 您可以使用它來讀取或寫入的最後一個項目，當您知道它存在。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_back_item.cpp   
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
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: back (STL/CLR)](../dotnet/vector-back-stl-clr.md)   
 [vector:: front (STL/CLR)](../dotnet/vector-front-stl-clr.md)   
 [vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)