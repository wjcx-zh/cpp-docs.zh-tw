---
title: "collection_adapter::iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::collection_adapter::iterator
dev_langs: C++
helpviewer_keywords: iterator member [STL/CLR]
ms.assetid: b1078abd-e766-464e-9dc6-32e95ab50695
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e485f79a8a6a6d260c18650118689ab35ab293f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="collectionadapteriterator-stlclr"></a>collection_adapter::iterator (STL/CLR)
受控制序列之迭代器的類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T1 iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T1`，可做為受控制序列的輸入迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_collection_adapter_iterator.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<配接器 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)