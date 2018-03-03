---
title: "vector::generic_container (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::generic_container
dev_langs:
- C++
helpviewer_keywords:
- generic_container member [STL/CLR]
ms.assetid: f291493f-dbdd-4240-935e-ce7432b59872
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f358fe0dffa0be848514bc741b57b88766b9d248
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vectorgenericcontainer-stlclr"></a>vector::generic_container (STL/CLR)
容器的泛型介面型別。  
  
## <a name="syntax"></a>語法  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IVector<generic_value>  
    generic_container;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述此樣板容器類別的泛型介面。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_generic_container.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualC.StlClr.IVector%601>   
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)   
 [vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)   
 [vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)