---
title: 運算子 ！ = (map) (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::operator!=
dev_langs:
- C++
helpviewer_keywords:
- operator!= member [STL/CLR]
ms.assetid: 335c3b24-27ed-4cc8-b49d-02b83ec5fd0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 66c3ac75105f22269acbd23497363d3dd4b84abc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operator-map-stlclr"></a>operator!= (map) (STL/CLR)
列出不相等比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator!=(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 使用它來測試是否`left`未經過排序相同`right`兩個對應時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_map_operator_ne.cpp   
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
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [運算子 = = (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)   
 [運算子\<(map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)   
 [運算子 > = (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)   
 [運算子 > (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)   
 [operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)