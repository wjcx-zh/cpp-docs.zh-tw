---
title: "&lt;ios&gt; 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::internal [C++]
- std::left [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: 60bb8bac5ca2f961d6d2977dc84d0844dfd54b8c
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt; 函式
||||  
|-|-|-|  
|[defaultfloat](#ios_defaultfloat)|[boolalpha](#boolalpha)|[dec](#dec)|  
|[fixed](#fixed)|[hex](#hex)|[internal](#internal)|  
|[left](#left)|[noboolalpha](#noboolalpha)|[noshowbase](#noshowbase)|  
|[noshowpoint](#noshowpoint)|[noshowpos](#noshowpos)|[noskipws](#noskipws)|  
|[nounitbuf](#nounitbuf)|[nouppercase](#nouppercase)|[oct](#oct)|  
|[right](#right)|[scientific](#scientific)|[showbase](#showbase)|  
|[showpoint](#showpoint)|[showpos](#showpos)|[skipws](#skipws)|  
|[unitbuf](#unitbuf)|[uppercase](#uppercase)|  
  
##  <a name="boolalpha"></a>  boolalpha  
 指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 **true** 或 **false**。  
  
```  
ios_base& boolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `bool` 類型的變數預設會顯示為 1 或 0。  
  
 `boolalpha` 有效率地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::boolalpha`)，然後傳回`str`。  
  
 [noboolalpha](../standard-library/ios-functions.md#noboolalpha) 會回復 `boolalpha` 的效果。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_boolalpha.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   bool b = true;  
   cout << b << endl;  
   boolalpha( cout );  
   cout << b << endl;  
   noboolalpha( cout );  
   cout << b << endl;  
   cout << boolalpha << b << endl;  
}  
```  
  
```Output  
1  
true  
1  
true  
```  
  
##  <a name="dec"></a>  dec  
 指定整數變數會以基底 10 標記法顯示。  
  
```  
ios_base& dec(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 整數變數預設會使用以 10 為底數的方式來顯示。  
  
 **dec** 會實際呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)( `ios_base::dec`**, ios_base::basefield**)，然後傳回 `str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_dec.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 100;  
  
   cout << i << endl;   // Default is base 10  
   cout << hex << i << endl;     
   dec( cout );  
   cout << i << endl;  
   oct( cout );  
   cout << i << endl;  
   cout << dec << i << endl;  
}  
```  
  
```Output  
100  
64  
100  
144  
100  
```  
  
##  <a name="ios_defaultfloat"></a>  &lt;ios&gt; defaultfloat  
 設定 `ios_base` 物件的旗標會使用浮點值的預設顯示格式。  
  
```  
ios_base& defaultfloat(ios_base& _Iosbase);
```  
  
### <a name="parameters"></a>參數  
 `_Iosbase`  
 `ios_base` 物件。  
  
### <a name="remarks"></a>備註  
 操作工具會實際呼叫 _I `osbase.`[ios_base::unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`，然後傳回 _I `osbase`。  
  
##  <a name="fixed"></a>  fixed  
 指定浮點數會以固定十進位標記法顯示。  
  
```  
ios_base& fixed(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 **fixed** 是浮點數的預設顯示標記法。 [scientific](../standard-library/ios-functions.md#scientific) 會讓浮點數以科學標記法顯示。  
  
 此操作工可有效地呼叫 * str.*[setf](../standard-library/ios-base-class.md#setf)( `ios_base::fixed`， **ios_base::floatfield**)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_fixed.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 1.1F;  
  
   cout << i << endl;   // fixed is the default  
   cout << scientific << i << endl;  
   cout.precision( 1 );  
   cout << fixed << i << endl;  
}  
```  
  
```Output  
1.1  
1.100000e+000  
1.1  
```  
  
##  <a name="hex"></a>  hex  
 指定整數變數應使用以 16 為底數的標記法來顯示。  
  
```  
ios_base& hex(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 整數變數預設會使用以 10 為底數的標記法來顯示。 [dec](../standard-library/ios-functions.md#dec) 和 [oct](../standard-library/ios-functions.md#oct) 也會變更整數變數的顯示方式。  
  
 操作工具會實際呼叫 `str`**.**[setf](../standard-library/ios-base-class.md#setf)( `ios_base::hex`, **ios_base::basefield**)，然後傳回 `str`。  
  
### <a name="example"></a>範例  
  如需如何使用 **hex** 的範例，請參閱 [dec](../standard-library/ios-functions.md#dec)。  
  
##  <a name="internal"></a>  internal  
 使數字的正負號靠左對齊，數字靠右對齊。  
  
```  
ios_base& internal(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 `str` 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [showpos](../standard-library/ios-functions.md#showpos) 會導致針對正數顯示正負號。  
  
 操作工具會實際呼叫 `str`. [setf](../standard-library/ios-base-class.md#setf)( [ios_base::internal](../standard-library/ios-base-class.md#fmtflags), [ios_base::adjustfield](../standard-library/ios-base-class.md#fmtflags))，然後傳回 `str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_internal.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
  
int main( void )   
{  
   using namespace std;  
   float i = -123.456F;  
   cout.fill( '.' );  
   cout << setw( 10 ) << i << endl;  
   cout << setw( 10 ) << internal << i << endl;  
}  
```  
  
```Output  
..-123.456  
-..123.456  
```  
  
##  <a name="left"></a>  left  
 使與輸出寬度不同寬的文字出現在具有左邊界的資料流排清中。  
  
```  
ios_base& left(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::left`， **ios_base::adjustfield**)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_left.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout.width( 20 );   
   cout << f1 << endl;  
   cout << left << f1 << endl;  
}  
```  
  
```Output  
                   5  
5  
```  
  
##  <a name="noboolalpha"></a>  noboolalpha  
 指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 0 或 1。  
  
```  
ios_base& noboolalpha(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `noboolalpha` 預設為啟用。  
  
 `noboolalpha` 有效率地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::boolalpha`)，然後傳回`str`。  
  
 [boolalpha](../standard-library/ios-functions.md#boolalpha) 會回復 `noboolalpha` 的效果。  
  
### <a name="example"></a>範例  
  如需使用 `noboolalpha` 的範例，請參閱 [boolalpha](../standard-library/ios-functions.md#boolalpha)。  
  
##  <a name="noshowbase"></a>  noshowbase  
 關閉指出據以顯示數字之標記基底的功能。  
  
```  
ios_base& noshowbase(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `noshowbase` 依預設為開啟。 請使用 [showbase](../standard-library/ios-functions.md#showbase) 來指出數字的標記底數。  
  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showbase`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  如需如何使用 `noshowbase` 的範例，請參閱 [showbase](../standard-library/ios-functions.md#showbase)。  
  
##  <a name="noshowpoint"></a>  noshowpoint  
 顯示小數部分為零之浮點數的整數部分。  
  
```  
ios_base& noshowpoint(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `noshowpoint` 預設為開啟；請使用 [showpoint](../standard-library/ios-functions.md#showpoint) 和 [precision](../standard-library/ios-base-class.md#precision) 來顯示小數點後的零。  
  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showpoint`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_noshowpoint.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.000;  
   cout << f1 << endl;   // noshowpoint is default  
   cout.precision( 4 );  
   cout << showpoint << f1 << endl;  
   cout << noshowpoint << f1 << endl;  
}  
```  
  
```Output  
5  
5.000  
5  
```  
  
##  <a name="noshowpos"></a>  noshowpos  
 使正數不明確標示正負號。  
  
```  
ios_base& noshowpos(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `noshowpos` 依預設為開啟。  
  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::showps`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  如需使用 `noshowpos` 的範例，請參閱 [showpos](../standard-library/ios-functions.md#showpos)。  
  
##  <a name="noskipws"></a>  noskipws  
 使輸入資料流讀取空格。  
  
```  
ios_base& noskipws(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [skipws](../standard-library/ios-functions.md#skipws) 預設為啟用。 在輸入資料流中讀取到空格時，即表示已達到緩衝區結尾。  
  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::skipws`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_noskipws.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
  
int main() {  
   using namespace std;     
   string s1, s2, s3;  
   cout << "Enter three strings: ";  
   cin >> noskipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;     
}  
```  
  
##  <a name="nounitbuf"></a>  nounitbuf  
 使輸出在緩衝區已滿時進行緩衝並繼續處理。  
  
```  
ios_base& nounitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [unitbuf](../standard-library/ios-functions.md#unitbuf) 會使得在緩衝區不為空時處理緩衝區。  
  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::unitbuf`)，然後傳回`str`。  
  
##  <a name="nouppercase"></a>  nouppercase  
 指定以小寫顯示十六進位數字和科學標記法中的指數。  
  
```  
ios_base& nouppercase(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 此操作工可有效地呼叫`str`。[unsetf](../standard-library/ios-base-class.md#unsetf)( `ios_base::uppercase`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  如需使用 `nouppercase` 的範例，請參閱 [uppercase](../standard-library/ios-functions.md#uppercase)。  
  
##  <a name="oct"></a>  oct  
 指定以基底 8 標記法顯示整數變數。  
  
```  
ios_base& oct(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 物件的參考從中*str*衍生。  
  
### <a name="remarks"></a>備註  
 整數變數預設會使用以 10 為底數的標記法來顯示。 [dec](../standard-library/ios-functions.md#dec) 和 [hex](../standard-library/ios-functions.md#hex) 也會變更整數變數的顯示方式。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::oct`， `ios_base::basefield`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  如需如何使用 **oct** 的範例，請參閱 [dec](../standard-library/ios-functions.md#dec)。  
  
##  <a name="right"></a>  right  
 使與輸出寬度不同寬的文字出現在具有右邊界的資料流排清中。  
  
```  
ios_base& right(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 物件的參考從中*str*衍生。  
  
### <a name="remarks"></a>備註  
 [left](../standard-library/ios-functions.md#left) 也會修改文字的對齊方式。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::right`， `ios_base::adjustfield`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_right.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   double f1= 5.00;  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << left << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
   cout.width( 20 );  
   cout << right << f1 << endl;  
   cout.width( 20 );  
   cout << f1 << endl;  
}  
```  
  
```Output  
5  
                   5  
5                     
5                     
                   5  
                   5  
```  
  
##  <a name="scientific"></a>  scientific  
 讓浮點數以科學標記法顯示。  
  
```  
ios_base& scientific(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [fixed](../standard-library/ios-functions.md#fixed) 標記法是浮點數的預設標記法。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::scientific`， `ios_base::floatfield`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_scientific.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   float i = 100.23F;  
  
   cout << i << endl;  
   cout << scientific << i << endl;  
}  
```  
  
```Output  
100.23  
1.002300e+002  
```  
  
##  <a name="showbase"></a>  showbase  
 指出據以顯示數字的標記基底。  
  
```  
ios_base& showbase(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 數字的標示底數可以藉由 [dec](../standard-library/ios-functions.md#dec)、[oct](../standard-library/ios-functions.md#oct) 或 [hex](../standard-library/ios-functions.md#hex) 來變更。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::showbase`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_showbase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int j = 100;  
  
   cout << showbase << j << endl;   // dec is default  
   cout << hex << j << showbase << endl;  
   cout << oct << j << showbase << endl;  
  
   cout << dec << j << noshowbase << endl;  
   cout << hex << j << noshowbase << endl;  
   cout << oct << j << noshowbase << endl;  
}  
```  
  
```Output  
100  
0x64  
0144  
100  
64  
144  
```  
  
##  <a name="showpoint"></a>  showpoint  
 顯示浮點數的整數部分和小數點右側的數字，即使小數部分為零亦然。  
  
```  
ios_base& showpoint(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [noshowpoint](../standard-library/ios-functions.md#noshowpoint) 預設為啟用。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::showpoint`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  如需使用 `showpoint` 的範例，請參閱 [noshowpoint](../standard-library/ios-functions.md#noshowpoint)。  
  
##  <a name="showpos"></a>  showpos  
 使正數明確標示正負號。  
  
```  
ios_base& showpos(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [noshowpos](../standard-library/ios-functions.md#noshowpos) 是預設值。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::showpos`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_showpos.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 1;  
  
   cout << noshowpos << i << endl;   // noshowpos is default  
   cout << showpos << i << endl;  
}  
```  
  
```Output  
1  
+1  
```  
  
##  <a name="skipws"></a>  skipws  
 使輸入資料流不讀取空格。  
  
```  
ios_base& skipws(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 _ *Str* 之物件的參考。  
  
### <a name="remarks"></a>備註  
 `skipws` 預設為啟用。 [noskipws](../standard-library/ios-functions.md#noskipws) 會導致從輸入資料流讀取空格。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( `ios_base::skipws`)，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   char s1, s2, s3;  
   cout << "Enter three characters: ";  
   cin >> skipws >> s1 >> s2 >> s3;  
   cout << "." << s1  << "." << endl;  
   cout << "." << s2 << "." << endl;  
   cout << "." << s3 << "." << endl;  
}  
```  
  
```Output  
  
1 2 3  
  
```  
  
```Output  
  
      1 2 3.1.  
.2.  
.3.  
```  
  
##  <a name="unitbuf"></a>  unitbuf  
 使輸出在緩衝區不為空時進行處理。  
  
```  
ios_base& unitbuf(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 `str` 之物件的參考。  
  
### <a name="remarks"></a>備註  
 請注意，`endl` 也會清除緩衝區。  
  
 [nounitbuf](../standard-library/ios-functions.md#nounitbuf) 預設為啟用。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( [ios_base::unitbuf](../standard-library/ios-base-class.md#fmtflags))，然後傳回`str`。  
  
##  <a name="uppercase"></a>  uppercase  
 指定以大寫顯示十六進位數字和科學標記法中的指數。  
  
```  
ios_base& uppercase(ios_base& str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。  
  
### <a name="return-value"></a>傳回值  
 對衍生 `str` 之物件的參考。  
  
### <a name="remarks"></a>備註  
 [nouppercase](../standard-library/ios-functions.md#nouppercase) 預設為啟用。  
  
 此操作工可有效地呼叫`str`。[setf](../standard-library/ios-base-class.md#setf)( [ios_base::uppercase](../standard-library/ios-base-class.md#fmtflags))，然後傳回`str`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_uppercase.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )   
{  
   using namespace std;  
  
   double i = 1.23e100;  
   cout << i << endl;  
   cout << uppercase << i << endl;  
  
   int j = 10;  
   cout << hex << nouppercase << j << endl;  
   cout << hex << uppercase << j << endl;  
}  
```  
  
```Output  
1.23e+100  
1.23E+100  
a  
A  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<ios>](../standard-library/ios.md)

