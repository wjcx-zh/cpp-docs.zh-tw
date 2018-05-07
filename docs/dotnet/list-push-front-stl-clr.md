---
title: 'list:: push_front (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::push_front
dev_langs:
- C++
helpviewer_keywords:
- push_front member [STL/CLR]
ms.assetid: 47525641-1139-44fc-ac62-bdc04876d9e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f1e196e70fba166b3017d0f7558afdea4c09645f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="listpushfront-stlclr"></a>list::push_front (STL/CLR)
加入新的第一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
void push_front(value_type val);  
```  
  
## <a name="remarks"></a>備註  
 成員函式插入值的項目`val`受控制序列的開頭。 您可以使用它前面加上另一個項目清單。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)   
 [list:: pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)   
 [list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)