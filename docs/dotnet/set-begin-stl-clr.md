---
title: 'set:: begin (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::begin
dev_langs:
- C++
helpviewer_keywords:
- begin member [STL/CLR]
ms.assetid: 4bfe0b50-bd7e-4b7a-81ba-143f40a7d916
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44a3333f9237fa7dcc43b48835c66272b6dd8402
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setbegin-stlclr"></a>set::begin (STL/CLR)
指定受控制序列的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回指定的受控制序列中，或空序列結尾之外的第一個元素的雙向迭代器。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列中，但其狀態的開頭。  
  
## <a name="example"></a>範例  
  
```  
// cliext_set_begin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)