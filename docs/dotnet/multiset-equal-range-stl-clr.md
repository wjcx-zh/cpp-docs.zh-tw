---
title: 'multiset:: equal_range (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::equal_range
dev_langs:
- C++
helpviewer_keywords:
- equal_range member [STL/CLR]
ms.assetid: 0fa617fb-8316-4310-b906-0322fa04aebe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a0e3f32ca87c934fce568d8f7a381fa07b5a427
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="multisetequalrange-stlclr"></a>multiset::equal_range (STL/CLR)
尋找符合指定之索引鍵的範圍。  
  
## <a name="syntax"></a>語法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
## <a name="remarks"></a>備註  
 成員函式會傳回迭代器的一組`cliext::pair<iterator, iterator>(` [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md) `(key),` [multiset:: upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)`(key))`。 您可以使用它來判斷目前在受控制序列中符合指定之索引鍵的項目範圍。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
typedef Mymultiset::pair_iter_iter Pairii;   
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
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [多重集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset:: count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)   
 [multiset:: find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)   
 [multiset:: lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)   
 [multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)