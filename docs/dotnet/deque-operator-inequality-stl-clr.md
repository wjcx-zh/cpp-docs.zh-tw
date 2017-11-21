---
title: "deque:: operator ！ = (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::operator!=
dev_langs: C++
helpviewer_keywords: operator!= member [STL/CLR]
ms.assetid: c23c7bd1-813e-4518-9947-eb13d1176a13
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d4b682b5d125f21e8212e2ac442caf51f8c2832e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="dequeoperator-stlclr"></a>deque::operator!= (STL/CLR)
Deque 不等於比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value>  
    bool operator!=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### <a name="parameters"></a>參數  
 `left`  
 要比較的左容器。  
  
 `right`  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`!(left == right)`。 使用它來測試是否`left`未經過排序相同`right`兩個 deque 時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_deque_operator_ne.cpp   
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
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [運算子 = = (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)   
 [運算子\<(deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [運算子 > = (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [運算子 > (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)   
 [operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)