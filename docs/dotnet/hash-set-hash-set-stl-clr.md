---
title: 'hash_set:: hash_set (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_set
dev_langs:
- C++
helpviewer_keywords:
- hash_set member [STL/CLR]
ms.assetid: 006414ed-db5a-4c08-ac81-4a8ae57d0aad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e0f8ce11d66b02c63d2eee6cf2022c16c214fe2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="hashsethashset-stlclr"></a>hash_set::hash_set (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_set();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`，並使用預設雜湊函式。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `explicit hash_set(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞和預設雜湊函數。  
  
 建構函式：  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_set(hash_set<Key>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)、 排序的述詞，預設值和預設雜湊函式。 您用它來指定 hash_set 物件所控制之序列的複本初始受控制的序列`right`使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_set(hash_set<Key>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)、 排序的述詞，預設值和預設雜湊函式。 您用它來指定 hash_set 物件所控制之序列的複本初始受控制的序列`right`使用預設排序述詞和雜湊函式。  
  
 建構函式：  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)、 排序的述詞，預設值和預設雜湊函式。 您可以使用它來製作受控制的序列的其他順序，排序述詞和雜湊函式的預設值。  
  
 建構函式：  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來製作受控制的序列的另一個序列，以指定順序的述詞和預設雜湊函數。  
  
 建構函式：  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來製作受控制的序列的另一個序列，以指定順序的述詞和雜湊函式。  
  
 建構函式：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`、 排序的述詞，預設值和預設雜湊函式。 您可以使用它來進行受控制的序列排序述詞和雜湊函式的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`，並使用預設雜湊函式。 您可以使用它來進行受控制的序列的列舉值，指定排序述詞和預設雜湊函式與所描述的另一個序列的複本。  
  
 建構函式：  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`，與雜湊函式`hashfn`。 您可以使用它來進行受控制的序列的列舉值，指定排序述詞和雜湊函式與所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/hash_set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)