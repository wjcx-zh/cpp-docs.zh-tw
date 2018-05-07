---
title: 運算子&lt;= （清單） (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::operator<=
dev_langs:
- C++
helpviewer_keywords:
- operator<= member [STL/CLR]
ms.assetid: af677e20-f529-4055-b101-af9728bc090b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d397e654876cfdea0ab9e3989ed9bc92c0fe1ff0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operatorlt-list-stlclr"></a>運算子&lt;= （清單） (STL/CLR)
小於或等於清單比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`!(right < left)`。 使用它來測試是否`left`未經過排序之後`right`兩份清單時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [運算子 = = （清單） (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)   
 [運算子 ！ = （清單） (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [運算子\<（清單） (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)   
 [運算子 > = （清單） (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)