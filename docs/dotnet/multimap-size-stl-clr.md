---
title: 'multimap:: size (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap::size
dev_langs:
- C++
helpviewer_keywords:
- size member [STL/CLR]
ms.assetid: 79a14142-a528-49ab-b4fd-340f5a4e70f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7aa20fe50baba9d7900e1ac91bdbc29fb0ad3d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130990"
---
# <a name="multimapsize-stlclr"></a>multimap::size (STL/CLR)
計算元素的數目。  
  
## <a name="syntax"></a>語法  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制序列的長度。 您可以使用它來判斷目前在受控制序列中的項目數。 如果您在意順序是否具有非零的大小，請參閱[multimap:: empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)`()`。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multimap_size.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymultimap::make_value(L'd', 4));   
    c1.insert(Mymultimap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/對應 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)