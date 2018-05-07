---
title: 'set:: const_iterator (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::const_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_iterator member [STL/CLR]
ms.assetid: de234ad4-d420-4da8-a13a-1aec8c337d8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 95d17008dbc80da3ddb0983d90b6a9dd9bf0a627
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setconstiterator-stlclr"></a>set::const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T2`，可做為受控制序列的常數的雙向迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)