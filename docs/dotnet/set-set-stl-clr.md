---
title: 'set:: set (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::set
dev_langs:
- C++
helpviewer_keywords:
- set member [STL/CLR]
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6de8bb2616cd403e150ace02210e57ed5a019445
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="setset-stlclr"></a>set::set (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `set();`  
  
 使用預設排序述詞，初始化受控制的序列的任何項目， `key_compare()`。 您可以使用它來指定空的初始受控制的序列，使用預設排序述詞。  
  
 建構函式：  
  
 `explicit set(key_compare^ pred);`  
  
 初始化受控制的序列沒有項目時，順序的述詞`pred`。 您可以使用它來指定空的初始受控制的序列，以指定順序的述詞。  
  
 建構函式：  
  
 `set(set<Key>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)，使用預設排序述詞。 您用它來指定是集合物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `set(set<Key>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)，使用預設排序述詞。 您用它來指定是集合物件所控制之序列的複本初始受控制的序列`right`，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，使用預設排序述詞。 您可以使用它來製作受控制的序列的其他順序，排序述詞的預設值。  
  
 建構函式：  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控制的序列與順序 [`first`， `last`)，與順序的述詞`pred`。 您可以使用它來進行受控制的序列的指定順序的述詞的另一個序列的複本。  
  
 建構函式：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，排序述詞的預設值。 您可以使用它來進行受控制的序列排序述詞的預設值所列舉值，描述的另一個序列的複本。  
  
 建構函式：  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`，順序的述詞`pred`。 您可以使用它來進行受控制的序列的列舉值，指定順序的述詞所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
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
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [設定 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)