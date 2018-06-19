---
title: deque::insert (STL/CLR) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: a3b86c46-e6a8-42d0-b642-5a8f05ddd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6819b1c2e1086c38b2bb1be8207a26afc85168d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109761"
---
# <a name="dequeinsert-stlclr"></a>deque::insert (STL/CLR)
將項目加入指定的位置。  
  
## <a name="syntax"></a>語法  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 `count`  
 要插入的元素數目。  
  
 `first`  
 要插入範圍的開頭。  
  
 `last`  
 要插入範圍的結尾。  
  
 `right`  
 若要插入的列舉型別。  
  
 `val`  
 要插入之項目的值。  
  
 `where`  
 在前面插入的容器中的位置。  
  
## <a name="remarks"></a>備註  
 每個成員函式所指向的項目之前插入`where`其餘運算元所指定受控制序列中中, 序列。  
  
 第一個成員函式插入值的項目`val`並傳回指定的新插入的元素的迭代器。 您可以使用它來插入迭代器指定的位置之前的單一項目。  
  
 第二個成員函式會插入 `val` 值的 `count` 個元素數重複。 您可以使用它來插入零或多個連續的項目也就是相同值的所有複本。  
  
 如果 `InIt` 是整數類型，第三個成員函式的行為即與 `insert(where, (size_type)first, (value_type)last)` 相同。 否則，它會插入序列 [`first`， `last`)。 您可以使用它來插入另一個序列中複製的零或多個連續的元素。  
  
 第四個成員函式會插入所指定的序列`right`。 您可以使用它來插入列舉所描述的順序。  
  
 當插入單一項目，項目複本數目中是線性的插入點之間距離越近序列結尾的項目數。 （當插入順序的任一端的一或多個項目，沒有項目複本會發生。）如果`InIt`是輸入的迭代器，第三個成員函式會有效地執行單一插入每個項目序列中。 否則，當插入`N`項目，項目複本數目中是線性`N`加上數字的項目插入點之間距離越近序列的結尾。  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_deque_insert.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)