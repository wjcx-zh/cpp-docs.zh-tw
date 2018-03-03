---
title: "multiset:: rbegin (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: beec0024-9565-4809-86f9-8b2c4e533923
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 454db96f4fe970870654734c410393dad8cb14fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multisetrbegin-stlclr"></a>multiset::rbegin (STL/CLR)
指定反向受控制序列的開頭。  
  
## <a name="syntax"></a>語法  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回指定受控制序列中，或空的序列開頭以外路徑的最後一個元素的反向迭代器。 因此，它會指定`beginning`反向序列。 您使用它來取得指定的迭代器`current`受控制序列的長度變更時，可以變更受控制的序列相反的順序出現，但其狀態的開頭。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymultiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)   
 [multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)   
 [multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)