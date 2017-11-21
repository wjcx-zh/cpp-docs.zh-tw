---
title: "vector:: capacity (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::capacity
dev_langs: C++
helpviewer_keywords: capacity member [STL/CLR]
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97693360d03f0c861f1c2f1b956fcbd136d7c6f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="vectorcapacity-stlclr"></a>vector::capacity (STL/CLR)
報表配置的儲存體容器的大小。  
  
## <a name="syntax"></a>語法  
  
```  
size_type capacity();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回目前配置給保留受控制的序列的值至少一樣大的儲存體[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`。 您可以使用它來判斷多少容器之前它就必須重新配置受控制序列的儲存體所能成長。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  
  
## <a name="description"></a>說明  
 請注意，實際的容量可能不同的值如下所示，這麼久所有`ok`測試報告 true。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)