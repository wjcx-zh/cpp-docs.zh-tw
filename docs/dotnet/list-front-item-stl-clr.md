---
title: "list::front_item (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::front_item
dev_langs: C++
helpviewer_keywords: front_item member [STL/CLR]
ms.assetid: c871873b-7745-442b-9760-9d8096fa8610
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0d280d84a6cec1c0024adc1b6223a75eb349f96
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="listfrontitem-stlclr"></a>list::front_item (STL/CLR)
存取第一個項目。  
  
## <a name="syntax"></a>語法  
  
```  
property value_type front_item;  
```  
  
## <a name="remarks"></a>備註  
 屬性存取受控制的序列必須為非空白的第一個項目。 您可以使用它來讀取或寫入第一個項目中，當您知道它存在。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_front_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: back (STL/CLR)](../dotnet/list-back-stl-clr.md)   
 [list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)   
 [list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)