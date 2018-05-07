---
title: 'map:: map (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map::map
dev_langs:
- C++
helpviewer_keywords:
- map member [STL/CLR]
ms.assetid: c91f699a-4742-4859-b2b3-c2a01a750bea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cd39f72c776065eadac713012440b9fe4701329a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mapmap-stlclr"></a>map::map (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `map();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞。  
  
 建構函式：  
  
 `explicit map(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞。  
  
 建構函式：  
  
 `map(map<Key, Mapped>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)，使用預設排序述詞。 您用它來指定對應的物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `map(map<Key, Mapped>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)，使用預設排序述詞。 您用它來指定對應的物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，使用預設排序述詞。 您可以使用它來製作受控制的序列的其他順序，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`。 您可以使用它來進行受控制的序列的指定順序的述詞的另一個序列的複本。  
  
 建構函式：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，排序述詞的預設值。 您可以使用它來進行受控制的序列排序述詞的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`。 您可以使用它來進行受控制的序列的列舉值，指定順序的述詞所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
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
  
## <a name="see-also"></a>另請參閱  
 [地圖 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)   
 [map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)