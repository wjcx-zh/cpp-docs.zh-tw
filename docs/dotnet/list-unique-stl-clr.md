---
title: 'list:: unique (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::unique
dev_langs:
- C++
helpviewer_keywords:
- unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5dbfab0fb53a4ca11128d01e7b32060c6428549
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137571"
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
移除通過指定測試的相鄰項目。  
  
## <a name="syntax"></a>語法  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>參數  
 pred  
 項目配對的比較子。  
  
## <a name="remarks"></a>備註  
 第一個成員函式會移除受控制的序列 （清除） 會比較每個項目等於其前面的項目--如果項目`X`位於項目之前`Y`和`X == Y`，成員函式會移除`Y`。 您使用它來移除某個複本的每個序列的相鄰元素的比較等。 請注意，如果受控制的序列經過排序，例如透過呼叫[list:: sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`，成員函式會將只有項目具有唯一值。 (也因此才名為終端方法)。  
  
 第二個成員函式的行為與第一個相同之處在於它會移除每個項目`Y`下列項目`X`其`pred(X, Y)`。 您可以使用它來移除符合述詞函式或您指定的委派相鄰元素的每一個子序列的所有副本。 請注意，如果受控制的序列經過排序，例如透過呼叫`sort(pred)`，成員函式會保留不具有對等順序，與任何其他項目項目。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [list:: remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)