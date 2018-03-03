---
title: "vector:: vector (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector member [STL/CLR]
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a321e18c9fc921e1d88961b4f282c29917fa7962
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="vectorvector-stlclr"></a>vector::vector (STL/CLR)
建構容器物件。  
  
## <a name="syntax"></a>語法  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 要插入的元素數目。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 要插入的物件或範圍。  
  
 val  
 要插入之項目的值。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `vector();`  
  
 初始化受控制的序列為沒有項目。 您可以用它來指定空的初始受控制的序列。  
  
 建構函式：  
  
 `vector(vector<Value>% right);`  
  
 初始化受控制的序列與順序 [`right.begin()`， `right.end()`)。 您用它來指定的向量物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `vector(vector<Value>^ right);`  
  
 初始化受控制的序列與順序 [`right->begin()`， `right->end()`)。 您用它來指定其控制代碼的向量物件所控制之序列的複本初始受控制的序列`right`。  
  
 建構函式：  
  
 `explicit vector(size_type count);`  
  
 初始化具有受控制的序列`count`項目每個值`value_type()`。 您使用它來填入項目容器全都具有預設值。  
  
 建構函式：  
  
 `vector(size_type count, value_type val);`  
  
 初始化具有受控制的序列`count`項目每個值`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 建構函式：  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 初始化受控制的序列與順序 [`first`， `last`)。 您可以使用它來進行受控制的序列的另一個序列的複本。  
  
 建構函式：  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化受控制的序列的列舉值所指定的順序與`right`。 您可以使用它來進行受控制的序列的列舉值所描述的另一個序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
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
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)