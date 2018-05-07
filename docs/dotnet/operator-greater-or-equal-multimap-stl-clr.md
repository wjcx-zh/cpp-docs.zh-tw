---
title: 運算子&gt;= (multimap) (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::operator>=
dev_langs:
- C++
helpviewer_keywords:
- operator>= member [STL/CLR]
ms.assetid: a9e2451b-476f-48ad-a305-50798c2991f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 66610c9ea53658c62b875aaf474eb49802d4b60c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operatorgt-multimap-stlclr"></a>運算子&gt;= (multimap) (STL/CLR)
清單大於或等於比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator>=(multimap<Key, Mapped>% left,  
        multimap<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`!(left` `<` `right)`。 使用它來測試是否`left`之前未經過排序`right`兩個的多重時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multimap_operator_ge.cpp   
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
  
// assign to a new container   
    Mymultimap c2;   
    c2.insert(Mymultimap::make_value(L'a', 1));   
    c2.insert(Mymultimap::make_value(L'b', 2));   
    c2.insert(Mymultimap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [d 4]  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [運算子 = = (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)   
 [運算子 ！ = (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)   
 [運算子\<(multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)   
 [運算子 > (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)   
 [operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)