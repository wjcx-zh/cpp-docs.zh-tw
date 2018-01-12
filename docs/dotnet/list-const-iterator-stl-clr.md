---
title: "list:: const_iterator (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::const_iterator
dev_langs: C++
helpviewer_keywords: const_iterator member [STL/CLR]
ms.assetid: 24e19077-02d2-456e-a3f1-7caaf0b6c974
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4927349bc0f6519bfaa2b64e8de89d8ad74a4b7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="listconstiterator-stlclr"></a>list::const_iterator (STL/CLR)
用於受控制序列的常數迭代器類型。  
  
## <a name="syntax"></a>語法  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>備註  
 此類型描述未指定類型的物件`T2`，可做為受控制序列的常數隨機存取迭代器。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)