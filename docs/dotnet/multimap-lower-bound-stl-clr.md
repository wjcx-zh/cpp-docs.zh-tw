---
title: "multimap:: lower_bound (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: b8f9b2c2-ebcd-4553-b410-75fd8d472a49
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1ac99d460062c1cc2aef8dabb90bf45b11467487
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multimaplowerbound-stlclr"></a>multimap::lower_bound (STL/CLR)
尋找符合指定之索引鍵的範圍開頭。  
  
## <a name="syntax"></a>語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
## <a name="remarks"></a>備註  
 成員函式判斷第一個項目`X`具有對等順序，來控制序列中`key`。 如果沒有這類元素存在，它會傳回[multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; 否則它會傳回迭代器，指定`X`。 您可以使用它來尋找項目序列的開頭目前受控制序列之符合指定之索引鍵。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multimap_lower_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymultimap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap:: count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)   
 [multimap:: equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)   
 [multimap:: find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)   
 [multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)