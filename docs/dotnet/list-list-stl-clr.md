---
title: "list:: list (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::list
dev_langs: C++
helpviewer_keywords: list member [STL/CLR]
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f5ed413ec892ebdf89fc903ac9a9f06e4f2d917a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="listlist-stlclr"></a>list::list (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 `count`  
 要插入的元素數目。  
  
 `first`  
 要插入範圍的開頭。  
  
 `last`  
 要插入範圍的結尾。  
  
 `right`  
 要插入的物件或範圍。  
  
 `val`  
 要插入之項目的值。  
  
## <a name="remarks"></a>備註  
  
 建構函式：  
  
 `list();`  
  
 初始化受控制的序列為沒有項目。 您可以用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `list(list<Value>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)。 您用它來指定初始受控制的序列的清單物件所控制之序列的複本`right`。  
  
 建構函式：  
  
 `list(list<Value>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)。 您用它來指定其控制代碼的清單物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `explicit list(size_type count);`  
  
 初始化具有受控制的序列`count`項目每個值`value_type()`。 您使用它來填入項目容器全都具有預設值。  
  
 建構函式：  
  
 `list(size_type count, value_type val);`  
  
 初始化具有受控制的序列`count`項目每個值`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 建構函式：  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)。 您可以使用它來進行受控制的序列的另一個序列的複本。  
  
 建構函式：  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`。 您可以使用它來進行受控制的序列的列舉值所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)   
 [list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)