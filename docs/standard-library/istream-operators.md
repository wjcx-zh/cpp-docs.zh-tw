---
title: "&lt;istream&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 7174da41-f301-4a34-b631-0ab918b188d2
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: f73a5e24fd3864a46ac0c50bbdb18a1089a4a05e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="ltistreamgt-operators"></a>&lt;istream&gt; 運算子
 
##  <a name="op_gt_gt"></a>  operator&gt;&gt;  
 從資料流中擷取字元和字串。  
  
```  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,   
    Elem* str);

template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr,   
    Elem& Ch);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    signed char* str);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    signed char& Ch);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    unsigned char* str);

template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr,   
    unsigned char& Ch);

template <class Elem, class Tr, class Type>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,  
    Type& val);
```  
  
### <a name="parameters"></a>參數  
 `Ch`  
 字元。  
  
 `Istr`  
 資料流。  
  
 `str`  
 字串。  
  
 `val`  
 類型。  
  
### <a name="return-value"></a>傳回值  
 資料流  
  
### <a name="remarks"></a>備註  
 `basic_istream` 類別也會定義數個擷取運算子。 如需詳細資訊，請參閱 [basic_istream::operator>>](../standard-library/basic-istream-class.md#op_gt_gt)。  
  
 範本函式：  
  
```cpp  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem* str);
```  
  
 最多會擷取 *N* - 1 個元素，並將其儲存在開頭為 _ *Str* 的陣列中。 如果 `Istr`. [width](../standard-library/ios-base-class.md#width) 大於零，則 *N* 為 `Istr`. **width**；否則它會是可宣告的最大 **Elem** 陣列的大小。 此函式一律會在所儲存的任何已擷取元素之後儲存 **Elem()** 值。 不論是在檔案結尾、在值為 **Elem**(0) (不擷取的值) 的字元上，還是在 [ws](../standard-library/istream-functions.md#ws) 會捨棄的任何元素 (不擷取的元素) 上，都會提前停止擷取。 如果此函式未擷取任何元素，則會呼叫 `Istr`. [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 在任何情況下，它都會呼叫 `Istr`. **width**(0)，並傳回 `Istr`。  
  
 **安全性注意事項**：要從輸入資料流中擷取的以 Null 結束字串不得超過目的緩衝區 `str` 的大小。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 範本函式：  
  
```cpp  
template <class Elem, class Tr>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<Elem, Tr>& Istr, Elem& Ch);
```  
  
 會擷取元素 (如果可能)，並將其儲存在 `Ch` 中。 否則會呼叫 **is**。 [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**)。 在任何情況下，它都會傳回 `Istr`。  
  
 範本函式：  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char* str);
```  
  
 會傳回 `Istr` >> ( `char`**\***) `str`。  
  
 範本函式：  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, signed char& Ch);
```  
  
 會傳回 `Istr` >> ( **char&**) `Ch`。  
  
 範本函式：  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char* str);
```  
  
 會傳回 `Istr` >> ( **char \***) `str`。  
  
 範本函式：  
  
```cpp  
template <class Tr>  
basic_istream<char, Tr>& operator>>(
    basic_istream<char, Tr>& Istr, unsigned char& Ch);
```  
  
 會傳回 `Istr` >> ( **char&**) `Ch`。  
  
 範本函式：  
  
```cpp  
template <class Elem, class Tr, class Type>  
basic_istream<Elem, Tr>& operator>>(
    basic_istream<char, Tr>&& Istr,  
    Type& val);
```  
  
 會傳回 `Istr` `>>` `val` (並將對 `Istr` 的 `rvalue reference` 轉換成程序中的 `lvalue`)。  
  
### <a name="example"></a>範例  
  
```cpp  
// istream_op_extract.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   ws( cin );  
   char c[10];  
  
   cin.width( 9 );  
   cin >> c;  
   cout << c << endl;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<istream>](../standard-library/istream.md)


