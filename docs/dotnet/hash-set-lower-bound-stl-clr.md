---
title: 'hash_set:: lower_bound (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: 54fe8ee5-1977-4192-9cc6-b51e84b03a16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f36f90a7585002610fa6d000130d14a616db7382
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127236"
---
# <a name="hashsetlowerbound-stlclr"></a>hash_set::lower_bound (STL/CLR)
尋找符合指定之索引鍵的範圍開頭。  
  
## <a name="syntax"></a>語法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>參數  
 key  
 要搜尋的索引鍵值。  
  
## <a name="remarks"></a>備註  
 成員函式判斷第一個項目`X`雜湊至相同的值區為受控制序列中`key`且具有對等順序，以`key`。 如果沒有這類元素存在，它會傳回[hash_set:: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`; 否則它會傳回迭代器，指定`X`。 您可以使用它來尋找項目序列的開頭目前受控制序列之符合指定之索引鍵。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set:: count (STL/CLR)](../dotnet/hash-set-count-stl-clr.md)   
 [hash_set:: equal_range (STL/CLR)](../dotnet/hash-set-equal-range-stl-clr.md)   
 [hash_set:: find (STL/CLR)](../dotnet/hash-set-find-stl-clr.md)   
 [hash_set::upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md)