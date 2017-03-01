---
title: "&lt;ostream&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: 15
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 44708461657101b1ddad7db76f1c3c8d4df07f3a
ms.lasthandoff: 02/24/2017

---
# <a name="ltostreamgt-functions"></a>&lt;ostream&gt; 函式
||||  
|-|-|-|  
|[swap](#swap)|[endl](#endl)|[ends](#ends)|  
|[flush](#flush)|  
  
##  <a name="a-nameendla--endl"></a><a name="endl"></a>  endl  
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
 操作工具呼叫 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#basic_ostream__put)( `Ostr`**.** [widen](../standard-library/basic-ios-class.md#basic_ios__widen)( **'\n'**))，然後呼叫 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#basic_ostream__flush)。 它會傳回 `Ostr`。  
  
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
  
##  <a name="a-nameendsa--ends"></a><a name="ends"></a>  ends  
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
 操作工具呼叫 `Ostr`**.**[put](../standard-library/basic-ostream-class.md#basic_ostream__put)( `Elem`( **'\0'**))。 它會傳回 `Ostr.`。  
  
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
  
##  <a name="a-nameflusha--flush"></a><a name="flush"></a>  flush  
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
 操作工具呼叫 `Ostr`**.**[flush](../standard-library/basic-ostream-class.md#basic_ostream__flush)。 它會傳回 `Ostr`。  
  
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
  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>  swap  
 交換兩個 `basic_ostream` 物件的值。  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_ostream<Elem, Tr>& left,  
    basic_ostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 `basic_ostream` 物件的 lvalue 參考。  
  
 ` right`  
 `basic_ostream` 物件的 lvalue 參考。  
  
### <a name="remarks"></a>備註  
 樣板函式 `swap` 會執行 ` left.swap(`` right``)`。  
  
## <a name="see-also"></a>另請參閱  
 [\<ostream>](../standard-library/ostream.md)


