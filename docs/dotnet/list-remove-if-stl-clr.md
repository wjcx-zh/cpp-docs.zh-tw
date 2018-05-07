---
title: 'list:: remove_if (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::remove_if
dev_langs:
- C++
helpviewer_keywords:
- remove_if member [STL/CLR]
ms.assetid: cbc66192-751b-41c5-b557-d5d7bbc2a840
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 53a6c12509e34e40d3a6a439fb03dc1f6779aba3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="listremoveif-stlclr"></a>list::remove_if (STL/CLR)
移除通過指定的測試的項目。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>參數  
 pred  
 若要移除的項目進行測試。  
  
## <a name="remarks"></a>備註  
 成員函式中移除受控制的序列 （清除） 從每個項目`X`其`pred(X)`為 true。 您可以使用它來移除所有項目滿足條件指定為函式或委派。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [list:: erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list:: remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)