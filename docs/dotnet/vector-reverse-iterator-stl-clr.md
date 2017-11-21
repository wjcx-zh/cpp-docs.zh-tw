---
title: "vector:: reverse_iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::reverse_iterator
dev_langs: C++
helpviewer_keywords: reverse_iterator member [STL/CLR]
ms.assetid: 0a90c5ee-a95f-4f71-a027-f1668000ccd4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04a4048c8ebb108efef9c4a6181f864eb2d9d708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="vectorreverseiterator-stlclr"></a>vector::reverse_iterator (STL/CLR)
受控制序列的反向迭代器類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型 `T3` 的物件，其可用作受控制序列的反向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)   
 [vector:: const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)   
 [vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)