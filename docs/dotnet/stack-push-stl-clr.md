---
title: 'stack:: push (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::push
dev_langs:
- C++
helpviewer_keywords:
- push member [STL/CLR]
ms.assetid: 60e5b076-c80f-4af0-a018-62cda7e081db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6236989d1bdcc9ee7f6705257c91e5509ae38878
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165385"
---
# <a name="stackpush-stlclr"></a>stack::push (STL/CLR)
加入新的最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
void push(value_type val);  
```  
  
## <a name="remarks"></a>備註  
 成員函式插入值的項目`val`受控制序列的結尾。 您可以使用它來附加至堆疊的另一個項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_stack_push.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<堆疊 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)