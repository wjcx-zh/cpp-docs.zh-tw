---
title: collection_adapter::base (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::collection_adapter::base
dev_langs:
- C++
helpviewer_keywords:
- base member [STL/CLR]
ms.assetid: 44928046-3fda-4974-817f-bc61a6f11b9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fe35a9f5eb0a005d2734ff0ab83eeaf75634e62f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="collectionadapterbase-stlclr"></a>collection_adapter::base (STL/CLR)
將指定的已包裝的 BCL 介面。  
  
## <a name="syntax"></a>語法  
  
```  
Coll^ base();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回儲存的 BCL 介面控制代碼。  
  
## <a name="example"></a>範例  
  
```  
// cliext_collection_adapter_base.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d6x(6, L'x');   
    Mycoll c1(%d6x);   
  
// display initial contents " x x x x x x"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("base() same = {0}", c1.base() == %c1);   
    return (0);   
    }  
  
```  
  
```Output  
 x x x x x x  
base() same = True  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<配接器 cliext/>  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)