---
title: "deque:: deque (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::deque::deque
dev_langs:
- C++
helpviewer_keywords:
- deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b077e4c92d9307b8ff99126c824d0a902ce1ff83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `deque();`  
  
 初始化受控制的序列為沒有項目。 您可以用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `deque(deque<Value>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)。 您用它來指定 deque 物件所控制之序列的複本初始受控制的序列`right`。 如需有關迭代器的詳細資訊，請參閱[deque:: begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)和[deque:: end (STL/CLR)](../dotnet/deque-end-stl-clr.md)。  
  
 建構函式：  
  
 `deque(deque<Value>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)。 您用它來指定其控制代碼的 deque 物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `explicit deque(size_type count);`  
  
 初始化具有受控制的序列`count`項目每個值`value_type()`。 您使用它來填入項目容器全都具有預設值。  
  
 建構函式：  
  
 `deque(size_type count, value_type val);`  
  
 初始化具有受控制的序列`count`項目每個值`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 建構函式：  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)。 您可以使用它來進行受控制的序列的另一個序列的複本。  
  
 建構函式：  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`。 您可以使用它來進行受控制的序列的列舉值所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)