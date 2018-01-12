---
title: "vector:: push_back (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::push_back
dev_langs: C++
helpviewer_keywords: push_back member [STL/CLR]
ms.assetid: 4a4c302b-e29f-4b68-b759-2f831814d896
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3721f967290b540dd03d1cab2d12a4d47f3b3f73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vectorpushback-stlclr"></a>vector::push_back (STL/CLR)
加入新的最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
void push_back(value_type val);  
```  
  
## <a name="remarks"></a>備註  
 成員函式插入值的項目`val`受控制序列的結尾。 您可以使用它來將另一個項目附加至向量。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_push_back.cpp   
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
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)