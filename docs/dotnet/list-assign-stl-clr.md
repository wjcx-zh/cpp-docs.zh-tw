---
title: "list:: assign (STL/CLR) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::assign
dev_langs: C++
helpviewer_keywords: assign member [STL/CLR]
ms.assetid: c5f2b131-d0e1-4188-9d4b-d617280e4032
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed13bb97aeceb0918d7b92405c9742a6f9710dc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="listassign-stlclr"></a>list::assign (STL/CLR)
取代所有項目。  
  
## <a name="syntax"></a>語法  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>參數  
 count  
 要插入的元素數目。  
  
 第一  
 要插入範圍的開頭。  
  
 last  
 要插入範圍的結尾。  
  
 向右  
 若要插入的列舉型別。  
  
 val  
 要插入之項目的值。  
  
## <a name="remarks"></a>備註  
 第一個成員函式取代重複的受控制的序列`count`值的項目`val`。 您使用它來填入項目容器全都具有相同的值。  
  
 如果`InIt`是整數類型，第二個成員函式的行為相同`assign((size_type)first, (value_type)last)`。 否則，它會取代受控制的序列的順序 [`first`， `last`)。 您使用它來進行受控制的序列複製另一個序列。  
  
 第三個成員函式的列舉值所指定的順序，取代受控制的序列`right`。 您可以使用它來製作受控制的序列的序列所描述的列舉值。  
  
## <a name="example"></a>範例  
  
```  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** \<cliext/清單 >  
  
 **命名空間：** cliext  
  
## <a name="see-also"></a>另請參閱  
 [清單 (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)