---
title: "map:: upper_bound (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::upper_bound
dev_langs: C++
helpviewer_keywords: upper_bound member [STL/CLR]
ms.assetid: d772b4a8-d0dc-439a-8b5b-3c91836d9256
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1058ee24eccbc06cf01db804ca0e715bacea4cbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mapupperbound-stlclr"></a>map::upper_bound (STL/CLR)
尋找符合指定之索引鍵的範圍結尾。  
  
## <a name="syntax"></a>語法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
## <a name="remarks"></a>備註  
 成員函式決定的最後一個項目`X`具有對等順序，來控制序列中`key`。 如果沒有這類元素存在，或如果`X`是最後一個項目，在受控制序列中，它會傳回[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; 否則它會傳回迭代器，指定之外的第一個項目`X`. 您可以使用它來目前受控制序列之符合指定之索引鍵中尋找的項目序列的結尾。  
  
## <a name="example"></a>範例  
  
```  
// cliext_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Mymap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map:: count (STL/CLR)](../dotnet/map-count-stl-clr.md)   
 [map:: equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)   
 [map:: find (STL/CLR)](../dotnet/map-find-stl-clr.md)   
 [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)