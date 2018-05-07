---
title: 'list:: splice (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::splice
dev_langs:
- C++
helpviewer_keywords:
- splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0c92faf6a4ec84e6ed65c58d02337038398d37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch 節點之間的連結。  
  
## <a name="syntax"></a>語法  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 若要連接之範圍的開頭。  
  
 last  
 若要連接之範圍的結尾。  
  
 向右  
 要從連接之容器。  
  
 其中  
 在之前所連接之容器中的位置。  
  
## <a name="remarks"></a>備註  
 第一個成員函式會插入所控制的序列`right`指向受控制序列中的項目之前`where`。 它也會移除 `right` 中的所有元素。 (`%right`不得等於`this`。)您可以使用它來 splice 一份清單的所有到另一個。  
  
 第二個成員函式中移除項目由指向`first`所控制的序列中`right`並將它插入之前所指向受控制序列中的項目`where`。 (如果`where` `==` `first` `||` `where` `== ++first`，不會發生變更。)您可以使用它來分離到另一份清單的單一項目。  
  
 第三個成員函式會插入所指定的子範圍 [`first`， `last`) 所控制序列中`right`指向受控制序列中的項目之前`where`。 它也會移除 `right` 所控制序列中的原始子範圍 (如果`right` `==` `this`，範圍 [`first`， `last`) 不能包含項目由指向`where`。)您可以使用它來分離到另一個清單中零個或多個項目的序列。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_splice.cpp   
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
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [list:: insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)