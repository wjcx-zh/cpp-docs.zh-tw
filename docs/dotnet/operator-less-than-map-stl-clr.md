---
title: "運算子&lt;(map) (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: 9ff87b44-663e-4b99-9dba-d775d9f6f853
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 73004f03191ba09eefdf1a0ea91dbdbe14d973d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="operatorlt-map-stlclr"></a>運算子&lt;(map) (STL/CLR)
清單小於比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式傳回 true，否則，最低的位置`i`其`!(right[i] < left[i])`是也是 true， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否`left`排序之前`right`兩個對應時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_map_operator_lt.cpp   
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
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [運算子 = = (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)   
 [運算子 ！ = (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)   
 [運算子 > = (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)   
 [運算子 > (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)   
 [operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)