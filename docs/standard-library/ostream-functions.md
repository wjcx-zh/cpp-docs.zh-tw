---
title: "&lt;ostream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 15
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 252a178f1ce71c30bdd830811cbce59b22acc791
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ends](#ends)|  
|[flush](#flush)|  
  
##  <a name="endl"></a>  endl  
 結束一行並清除緩衝區。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& endl(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>參數  
 `Elem`  
 元素類型。  
  
 `Ostr`  
 `basic_ostream` 類型的物件。  
  
 `Tr`  
 字元特性。  
  
### <a name="return-value"></a>傳回值  
 `basic_ostream` 類型的物件。  
  
### <a name="remarks"></a>備註  
 操作工具呼叫 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Ostr`**.** [widen](../standard-library/basic-ios-class.md#widen)( **'\n'**))，然後呼叫 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush)。 它會傳回 `Ostr`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ostream_endl.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << endl;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="ends"></a>  ends  
 結束字串。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& ends(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>參數  
 `Elem`  
 元素類型。  
  
 `Ostr`  
 `basic_ostream` 類型的物件。  
  
 `Tr`  
 字元特性。  
  
### <a name="return-value"></a>傳回值  
 `basic_ostream` 類型的物件。  
  
### <a name="remarks"></a>備註  
 操作工具呼叫 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#put)( `Elem`( **'\0'**))。 它會傳回 `Ostr.`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ostream_ends.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "a";  
   cout << "b" << ends;  
   cout << "c" << endl;  
}  
```  
  
```Output  
ab c  
```  
  
##  <a name="flush"></a>  flush  
 清除緩衝區。  
  
```  
template class<Elem, Tr> basic_ostream<Elem, Tr>& flush(basic_ostream<Elem, Tr>& Ostr);
```  
  
### <a name="parameters"></a>參數  
 `Elem`  
 元素類型。  
  
 `Ostr`  
 `basic_ostream` 類型的物件。  
  
 `Tr`  
 字元特性。  
  
### <a name="return-value"></a>傳回值  
 `basic_ostream` 類型的物件。  
  
### <a name="remarks"></a>備註  
 操作工具呼叫 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#flush)。 它會傳回 `Ostr`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "testing" << flush;  
}  
```  
  
```Output  
testing  
```  
  
##  <a name="swap"></a>  swap  
 交換兩個 `basic_ostream` 物件的值。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `basic_ostream` 物件的 lvalue 參考。  
  
 `right`  
 `basic_ostream` 物件的 lvalue 參考。  
  
### <a name="remarks"></a>備註  
 樣板函式 `swap` 會執行 `left.swap(right)`。  
  
## <a name="see-also"></a>另請參閱  
 [\<ostream>](../standard-library/ostream.md)


