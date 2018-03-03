---
title: "multimap:: multimap (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap::multimap
dev_langs:
- C++
helpviewer_keywords:
- multimap member [STL/CLR]
ms.assetid: cdf9c5dc-774c-424e-aeea-7554643e401c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6ab4f50af1a7fd161ec192890fb7be3134ad4c72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multimapmultimap-stlclr"></a>multimap::multimap (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
multimap();  
explicit multimap(key_compare^ pred);  
multimap(multimap<Key, Mapped>% right);  
multimap(multimap<Key, Mapped>^ right);  
template<typename InIter>  
    multimapmultimap(InIter first, InIter last);  
template<typename InIter>  
    multimap(InIter first, InIter last,  
        key_compare^ pred);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 pred  
 排序受控制序列的述詞。  
  
 向右  
 要插入的物件或範圍。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `multimap();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞。  
  
 建構函式：  
  
 `explicit multimap(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞。  
  
 建構函式：  
  
 `multimap(multimap<Key, Mapped>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)，使用預設排序述詞。 您用它來指定多重對應物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `multimap(multimap<Key, Mapped>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)，使用預設排序述詞。 您用它來指定多重對應物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> multimap(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，使用預設排序述詞。 您可以使用它來製作受控制的序列的其他順序，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> multimap(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`。 您可以使用它來進行受控制的序列的指定順序的述詞的另一個序列的複本。  
  
 建構函式：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，排序述詞的預設值。 您可以使用它來進行受控制的序列排序述詞的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`。 您可以使用它來進行受控制的序列的列舉值，指定順序的述詞所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
// construct an empty container   
    Mymultimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultimap c3(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3);   
    for each (Mymultimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultimap c7(c4);   
    for each (Mymultimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymultimap c8(%c3);   
    for each (Mymultimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)