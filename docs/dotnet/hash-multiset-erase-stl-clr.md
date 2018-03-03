---
title: "hash_multiset:: erase (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: bddd329d-aece-4b93-8355-005351c3aa45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e2e35eeecab632371922705cc95848e84a46d1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultiseterase-stlclr"></a>hash_multiset::erase (STL/CLR)
移除位於指定位置的項目。  
  
## <a name="syntax"></a>語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要清除範圍的開頭。  
  
 key  
 若要清除的機碼值。  
  
 last  
 若要清除的範圍的結尾。  
  
 其中  
 若要清除的項目。  
  
## <a name="remarks"></a>備註  
 第一個成員函式中移除指向受控制序列的項目`where`，並傳回指定移除的項目之外剩餘的第一個元素的迭代器或[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`如果沒有這類元素存在。 您可以使用它來移除單一項目。  
  
 第二個成員函式範圍中移除受控制序列的項目 [`first`， `last`)，並傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或`end()`如果沒有這個項目存在... 您可以使用它來移除零或多個連續的項目。  
  
 第三個成員函式中移除索引鍵具有對等順序受控制任何的序列項目至`key`，並傳回已移除項目的數目的計數。 您可以使用它來移除並計算所有符合指定之索引鍵的項目。  
  
 每個項目清除接受受控制序列的項目數目對數值成比例的時間。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::clear (STL/CLR)](../dotnet/hash-multiset-clear-stl-clr.md)