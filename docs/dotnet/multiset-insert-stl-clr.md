---
title: 'multiset:: insert (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: 7a3b1cc8-ec60-4ed0-ace5-46cb5872e6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed7be7302b1dcef069dc1e786e59e87755366613
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135300"
---
# <a name="multisetinsert-stlclr"></a>multiset::insert (STL/CLR)
加入項目。  
  
## <a name="syntax"></a>語法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 val  
 要插入索引鍵的值。  
  
 其中  
 若要插入 （只有提示） 的容器中的位置。  
  
## <a name="remarks"></a>備註  
 每個成員函式插入其餘運算元所指定的順序。  
  
 第一個成員函式插入值的項目`val`，並傳回指定的新插入的元素的迭代器。 您可以使用它來插入單一項目。  
  
 第二個成員函式插入值的項目`val`，並使用`where`做為提示 （若要改善效能），並傳回指定的新插入的元素的迭代器。 您可以使用它來插入這可能是您知道的項目旁的單一項目。  
  
 第三個成員函式會插入序列 [`first`， `last`)。 您可以使用它來插入其他順序從複製的零或多個項目。  
  
 第四個成員函式會插入所指定的序列`right`。 您可以使用它來插入列舉所描述的順序。  
  
 每個項目插入將會受控制序列中的項目數目對數值成比例的時間。 可能會插入在平攤常數時間，不過，給定的指定項目插入點至相鄰的提示。  
  
## <a name="example"></a>範例  
  
```  
// cliext_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/set >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)