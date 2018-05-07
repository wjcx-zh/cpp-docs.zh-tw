---
title: 'vector:: resize (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: a3556fbc-67d9-463a-9ffc-cb43ee15657f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f7327b62906746ef3bb561d88f8c6ddc2134aa65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="vectorresize-stlclr"></a>vector::resize (STL/CLR)
變更項目數目。  
  
## <a name="syntax"></a>語法  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>參數  
 new_size  
 新的受控制序列的大小。  
  
 val  
 填補項目的值。  
  
## <a name="remarks"></a>備註  
 成員函式同時確保[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()`從此以後傳回`new_size`。 如果第一個成員函式必須讓受控制的序列更長，即會將 `value_type()` 值附加至元素，而第二個成員函式會將 `val` 值附加至元素。 若要使較短的受控制的序列，這兩個成員函式有效地清除最後一個項目[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size`時間。 您使用它來確保受控制的序列的大小`new_size`、 修剪或填補目前受控制的序列。  
  
## <a name="example"></a>範例  
  
```  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<向量 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [向量 (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector:: clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)   
 [vector:: erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)   
 [vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)