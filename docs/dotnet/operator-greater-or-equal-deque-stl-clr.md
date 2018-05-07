---
title: 運算子&gt;= (deque) (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::operator>=
dev_langs:
- C++
helpviewer_keywords:
- operator>= member [STL/CLR]
ms.assetid: 14746073-60a3-4088-b7ea-f987e963d418
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 98e7e13bcf25c5332751ac56cf83ffe36d962ad2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operatorgt-deque-stlclr"></a>運算子&gt;= (deque) (STL/CLR)
Deque 大於或等於比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator>=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`!(left` `<` `right)`。 使用它來測試是否`left`之前未經過排序`right`兩個 deque 時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_deque_operator_ge.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [運算子 = = (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)   
 [deque:: operator ！ = (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)   
 [運算子\<(deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [運算子 > (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)   
 [operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)