---
title: "list:: resize (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::resize
dev_langs: C++
helpviewer_keywords: resize member [STL/CLR]
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ca91c9764f1fe438d0d7dfb66c52797d5d97aae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="listresize-stlclr"></a>list::resize (STL/CLR)
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
 成員函式同時確保[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()`從此以後傳回`new_size`。 如果第一個成員函式必須讓受控制的序列更長，即會將 `value_type()` 值附加至元素，而第二個成員函式會將 `val` 值附加至元素。 若要使較短的受控制的序列，這兩個成員函式有效地清除最後一個項目[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size`時間。 您使用它來確保受控制的序列的大小`new_size`、 修剪或填補目前受控制的序列。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
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
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list:: erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)