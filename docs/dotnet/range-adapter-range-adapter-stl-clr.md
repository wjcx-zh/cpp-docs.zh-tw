---
title: "range_adapter::range_adapter (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::range_adapter::range_adapter
dev_langs:
- C++
helpviewer_keywords:
- range_adapter member [STL/CLR]
ms.assetid: b16af13f-3358-4e82-927d-d0d4986bcb18
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3a8b93b6a02a2ad0db7282f7e5e8e3159dd23add
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rangeadapterrangeadapter-stlclr"></a>range_adapter::range_adapter (STL/CLR)
建構的配置器物件。  
  
## <a name="syntax"></a>語法  
  
```  
range_adapter();  
range_adapter(range_adapter<Iter>% right);  
range_adapter(range_adapter<Iter>^ right);  
range_adapter(Iter first, Iter last);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 換行的第一個迭代器。  
  
 last  
 換行的第二個迭代器。  
  
 向右  
 要複製的物件。  
  
## <a name="remarks"></a>備註  
 建構函式：  
  
 `range_adapter();`  
  
 初始化具有預設建構迭代器的預存迭代器組。  
  
 建構函式：  
  
 `range_adapter(range_adapter<Iter>% right);`  
  
 藉由複製的組儲存在初始化預存迭代器組`right`。  
  
 建構函式：  
  
 `range_adapter(range_adapter<Iter>^ right);`  
  
 藉由複製的組儲存在初始化預存迭代器組`*right`。  
  
 建構函式：  
  
 `range_adapter(Iter^ first, last);`  
  
 初始化具有預存迭代器組`first`和`last`。  
  
## <a name="example"></a>範例  
  
```  
// cliext_range_adapter_construct.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::deque<wchar_t> Mycont;   
typedef cliext::range_adapter<Mycont::iterator> Myrange;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
  
// construct an empty adapter   
    Myrange c1;   
  
// construct with an iterator pair   
    Myrange c2(d1.begin(), d1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another adapter   
    Myrange c3(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying an adapter handle   
    Myrange c4(%c3);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<配接器 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)   
 [range_adapter::operator= (STL/CLR)](../dotnet/range-adapter-operator-assign-stl-clr.md)