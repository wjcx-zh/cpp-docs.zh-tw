---
title: 'stack:: top (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::top
dev_langs:
- C++
helpviewer_keywords:
- top member [STL/CLR]
ms.assetid: 5d8b7b69-336e-4d01-8b91-413a17aa2533
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6380734e456db587c06bd273ecec0a5987eaed1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163327"
---
# <a name="stacktop-stlclr"></a>stack::top (STL/CLR)
存取最後一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
reference top();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列必須為非空白的最後一個元素的參考。 您可以使用它來存取最後一個項目中，當您知道它存在。  
  
## <a name="example"></a>範例  
  
```  
// cliext_stack_top.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top() = {0}", c1.top());   
  
// alter last item and reinspect   
    c1.top() = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
top() = c  
 a b x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<堆疊 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [堆疊 (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)