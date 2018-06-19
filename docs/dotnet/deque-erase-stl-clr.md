---
title: 'deque:: erase (STL/CLR) |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 831fbc2b-604f-446b-88bc-b37531304c33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5afcc69c27cf96f31d85b4c48d57540669941cbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110178"
---
# <a name="dequeerase-stlclr"></a>deque::erase (STL/CLR)
移除位於指定位置的項目。  
  
## <a name="syntax"></a>語法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>參數  
 `first`  
 要清除範圍的開頭。  
  
 `last`  
 若要清除的範圍的結尾。  
  
 `where`  
 若要清除的項目。  
  
## <a name="remarks"></a>備註  
 第一個成員函式會移除 `where` 所指向之受控制序列中的項目。 您可以使用它來移除單一項目。  
  
 第二個成員函式會移除 [`first`, `last`) 範圍中受控制序列中的元素。 您可以使用它來移除零或多個連續的項目。  
  
 這兩個成員函式會傳回指定任何移除的項目之外剩餘的第一個元素的迭代器或[deque:: end (STL/CLR)](../dotnet/deque-end-stl-clr.md) `()`如果沒有這類元素存在。  
  
 當清除項目，項目複本數目中是線性清除結尾之間距離越近序列結尾的項目數。 （當清除序列的任一端的一或多個項目，沒有項目複本會發生。）  
  
## <a name="example"></a>範例  
  
```cpp  
// cliext_deque_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::deque<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/deque >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)