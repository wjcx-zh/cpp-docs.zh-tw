---
title: 運算子&lt;(multiset) (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: 48150cda-4f3e-4535-860c-89f622a7f0a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d2c665161d266f64cf35b5802c0deca0f3e125df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operatorlt-multiset-stlclr"></a>運算子&lt;(multiset) (STL/CLR)
清單小於比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Key>  
    bool operator<(multiset<Key>% left,  
        multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式傳回 true，否則，最低的位置`i`其`!(right[i] < left[i])`是也是 true， `left[i] < right[i]`。 否則，它會傳回`left->size() < right->size()`使用它來測試是否`left`排序之前`right`兩個 （semantics） 與項目所比較的項目時。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_operator_lt.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2.insert(L'a');   
    c2.insert(L'b');   
    c2.insert(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [運算子 = = (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)   
 [運算子 ！ = (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)   
 [運算子 > = (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)   
 [運算子 > (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)   
 [operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)