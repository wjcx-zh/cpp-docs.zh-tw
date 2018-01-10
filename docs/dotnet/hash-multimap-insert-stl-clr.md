---
title: "hash_multimap:: insert (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::insert
dev_langs: C++
helpviewer_keywords: insert member [STL/CLR]
ms.assetid: 51cd98b0-c959-4a44-b914-582c00681bd7
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6b0535c43ebc3e1a969f19c5d2779b54c90aa397
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimapinsert-stlclr"></a>hash_multimap::insert (STL/CLR)
加入項目。  
  
## <a name="syntax"></a>語法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 val  
 要插入索引鍵的值。  
  
 其中  
 若要插入 （只有提示） 的容器中的位置。  
  
## <a name="remarks"></a>備註  
 每個成員函式插入其餘運算元所指定的順序。  
  
 第一個成員函式插入值的項目`val`，並傳回指定的新插入的元素的迭代器。 您可以使用它來插入單一項目。  
  
 第二個成員函式插入值的項目`val`，並使用`where`做為提示 （若要改善效能），並傳回指定的新插入的元素的迭代器。 您可以使用它來插入這可能是您知道的項目旁的單一項目。  
  
 第三個成員函式會插入序列 [`first`， `last`)。 您可以使用它來插入其他順序從複製的零或多個項目。  
  
 第四個成員函式會插入所指定的序列`right`。 您可以使用它來插入列舉所描述的順序。  
  
 每個項目插入將會受控制序列中的項目數目對數值成比例的時間。 可能會插入在平攤常數時間，不過，給定的指定項目插入點至相鄰的提示。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multimap_insert.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Myhash_multimap::iterator it =   
        c1.insert(Myhash_multimap::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",   
        it->first, it->second);   
  
    it = c1.insert(Myhash_multimap::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",   
        it->first, it->second);   
  
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    it = c1.insert(c1.begin(), Myhash_multimap::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multimap c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multimap c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Myhash_multimap::value_type>^)%c1);   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [x 24]  
insert([L'b' 2]) = [b 2]  
 [a 1] [b 2] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [b 2] [c 3] [x 24] [y 25]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)