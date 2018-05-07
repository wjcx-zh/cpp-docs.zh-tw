---
title: 運算子&gt;（佇列） (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::operator>
dev_langs:
- C++
helpviewer_keywords:
- operator> member [STL/CLR]
ms.assetid: 40396a01-b2b6-4921-a1eb-f8704b015b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bc14fe35a6830a57648e7f6e8002be095b2a89b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="operatorgt-queue-stlclr"></a>運算子&gt;（佇列） (STL/CLR)
佇列大於此數目比較。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>參數  
 左  
 要比較的左容器。  
  
 向右  
 要比較的右容器。  
  
## <a name="remarks"></a>備註  
 運算子函式會傳回`right` `<` `left`。 使用它來測試是否`left`排序後`right`兩個佇列時項目所比較的項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_queue_operator_gt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/佇列 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [佇列 (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [運算子 = = （佇列） (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)   
 [運算子 ！ = (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [運算子\<（佇列） (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [運算子 > = (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)