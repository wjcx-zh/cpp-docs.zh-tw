---
title: "hash_multimap:: hash_multimap (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multimap::hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap member [STL/CLR]
ms.assetid: a1d576a7-5dc7-4ad9-abef-ee7a13caaec3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cff49bfad9143663e8fe5d895c885918bff4a7a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimaphashmultimap-stlclr"></a>hash_multimap::hash_multimap (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
hash_multimap();  
explicit hash_multimap(key_compare^ pred);  
hash_multimap(key_compare^ pred, hasher^ hashfn);  
hash_multimap(hash_multimap<Key, Mapped>% right);  
hash_multimap(hash_multimap<Key, Mapped>^ right);  
template<typename InIter>  
    hash_multimaphash_multimap(InIter first, InIter last);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 hashfn  
 雜湊值區的對應索引鍵的函式。  
  
 last  
 要插入範圍的結尾。  
  
 pred  
 排序受控制序列的述詞。  
  
 向右  
 要插入的物件或範圍。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `hash_multimap();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`，並使用預設雜湊函式。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `explicit hash_multimap(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞和預設雜湊函數。  
  
 建構函式：  
  
 `hash_multimap(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_multimap(hash_multimap<Key, Mapped>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)、 排序的述詞，預設值和預設雜湊函式。 您用它來指定 hash_multimap 物件所控制之序列的複本初始受控制的序列`right`使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_multimap(hash_multimap<Key, Mapped>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)、 排序的述詞，預設值和預設雜湊函式。 您用它來指定 hash_multimap 物件所控制之序列的複本初始受控制的序列`right`使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)、 排序的述詞，預設值和預設雜湊函式。 您可以使用它來製作受控制的序列的其他順序，排序述詞和雜湊函式的預設值。  
  
 建構函式：  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來製作受控制的序列的另一個序列，以指定順序的述詞和預設雜湊函數。  
  
 建構函式：  
  
 `template<typename InIter> hash_multimap(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來製作受控制的序列的另一個序列，以指定順序的述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`、 排序的述詞，預設值和預設雜湊函式。 您可以使用它來進行受控制的序列排序述詞和雜湊函式的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來進行受控制的序列的列舉值，指定排序述詞和預設雜湊函式與所描述的另一個序列的複本。  
  
 建構函式：  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來進行受控制的序列的列舉值，指定排序述詞和雜湊函式與所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
// construct an empty container   
    Myhash_multimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multimap c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multimap c3(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multimap c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3);   
    for each (Myhash_multimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multimap c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multimap c7(c4);   
    for each (Myhash_multimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_multimap c8(%c3);   
    for each (Myhash_multimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_map >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)   
 [hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)