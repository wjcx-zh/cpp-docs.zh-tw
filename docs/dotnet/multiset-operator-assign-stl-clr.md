---
title: multiset::operator = (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= member [STL/CLR]
ms.assetid: 74e60042-d0d6-471f-8fdb-79b3c6856440
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1661f47399aa8fc4d1ddeeef546855bb16ac71cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multisetoperator-stlclr"></a>multiset::operator= (STL/CLR)
取代受控制的序列。  
  
## <a name="syntax"></a>語法  
  
```  
multiset<Key>% operator=(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>參數  
 向右  
 要複製的容器。  
  
## <a name="remarks"></a>備註  
 成員運算子複製`right`物件，然後傳回`*this`。 您使用它將受控制序列取代為 `right` 中受控制序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_operator_as.cpp   
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
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Mymultiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)