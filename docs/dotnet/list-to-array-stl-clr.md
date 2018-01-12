---
title: "list::to_array (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::to_array
dev_langs: C++
helpviewer_keywords: to_array member [STL/CLR]
ms.assetid: 3ea7b90c-127b-43cd-804b-019b86b77582
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ef25a5f7dd53524b21862dc7fdb4ebee5bb6d178
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="listtoarray-stlclr"></a>list::to_array (STL/CLR)
將受控制的序列複製到新的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
cli::array<Value>^ to_array();  
```  
  
## <a name="remarks"></a>備註  
 成員函式會傳回受控制的序列的陣列。 您可以使用它來取得陣列的形式受控制序列的複本。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_to_array.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c d  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>請參閱  
 [list (STL/CLR)](../dotnet/list-stl-clr.md)