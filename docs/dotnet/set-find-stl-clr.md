---
title: 'set:: find (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::find
dev_langs:
- C++
helpviewer_keywords:
- find member [STL/CLR]
ms.assetid: 916e581c-2815-4c07-a51a-6c5ddfa730c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4ec8c6daa61cde042dd928cfb4fea50224b44547
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setfind-stlclr"></a>set::find (STL/CLR)
尋找符合指定之索引鍵的元素。  
  
## <a name="syntax"></a>語法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
## <a name="remarks"></a>備註  
 受控制序列中的至少一個項目是否具有對等順序`key`，成員函式會傳回指定其中一個這些項目的迭代器，否則它會傳回[set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`。 您可以使用它來尋找元素目前受控制序列之符合指定之索引鍵。  
  
## <a name="example"></a>範例  
  
```  
// cliext_set_find.cpp   
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
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
```  
  
## <a name="description"></a>描述  
 請注意，`find`不保證它找到的數個項目。  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set:: equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)   
 [set:: lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)   
 [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)