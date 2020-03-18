---
title: '&lt;ios&gt; 函式'
ms.date: 11/04/2016
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
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
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
ms.openlocfilehash: c3b1e2350d0923cbfddf95492842ae126859e29f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421608"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt; 函式

## <a name="boolalpha"></a>boolAlpha

指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 **true** 或 **false**。

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

根據預設， **bool**類型的變數會顯示為1或0。

`boolalpha` 會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)（`ios_base::boolalpha`），然後傳回*str*。

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

## <a name="dec"></a>十進位

指定整數變數會以基底 10 標記法顯示。

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

整數變數預設會使用以 10 為底數的方式來顯示。

`dec` 會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)（`ios_base::dec`，`ios_base::basefield`），然後傳回*str*。

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

## <a name="ios_defaultfloat"></a>&lt;ios&gt; defaultfloat

設定 `ios_base` 物件的旗標會使用浮點值的預設顯示格式。

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>參數

*_Iosbase*\
`ios_base` 物件。

### <a name="remarks"></a>備註

操作工具會有效地呼叫 `iosbase.`[ios_base：： unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`，然後傳回*iosbase*。

## <a name="fixed"></a>固定匯率

指定浮點數會以固定十進位標記法顯示。

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`fixed` 是浮點數的預設顯示標記法。 [scientific](../standard-library/ios-functions.md#scientific) 會讓浮點數以科學標記法顯示。

操作工具會有效地呼叫*str*。[setf](../standard-library/ios-base-class.md#setf)（`ios_base::fixed`，`ios_base::floatfield`），然後傳回*str*。

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

## <a name="hex"></a>進制

指定整數變數應使用以 16 為底數的標記法來顯示。

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

整數變數預設會使用以 10 為底數的標記法來顯示。 [dec](../standard-library/ios-functions.md#dec) 和 [oct](../standard-library/ios-functions.md#oct) 也會變更整數變數的顯示方式。

操作工具會有效地呼叫 `str` **。** [setf](../standard-library/ios-base-class.md#setf)（`ios_base::hex`，`ios_base::basefield`），然後傳回*str*。

### <a name="example"></a>範例

如需如何使用 `hex`的範例，請參閱[dec](../standard-library/ios-functions.md#dec) 。

## <a name="hexfloat"></a>hexfloat

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a>內部

使數字的正負號靠左對齊，數字靠右對齊。

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[showpos](../standard-library/ios-functions.md#showpos) 會導致針對正數顯示正負號。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：： internal](../standard-library/ios-base-class.md#fmtflags)`, `[ios_base：： adjustfield](../standard-library/ios-base-class.md#fmtflags)`)`，然後傳回*str*。

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

## <a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a>左面

使與輸出寬度不同寬的文字出現在具有左邊界的資料流排清中。

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`，然後傳回*str*。

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

## <a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a>noboolAlpha

指定讓 [bool](../cpp/bool-cpp.md) 類型的變數在資料流中顯示為 0 或 1。

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`noboolalpha` 預設為啟用。

`noboolalpha` 會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`，然後傳回*str*。

[boolalpha](../standard-library/ios-functions.md#boolalpha) 會回復 `noboolalpha` 的效果。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/ios-functions.md#boolalpha)boolalpha`noboolalpha`。

## <a name="noshowbase"></a>noshowbase

關閉指出據以顯示數字之標記基底的功能。

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`noshowbase` 。 請使用 [showbase](../standard-library/ios-functions.md#showbase) 來指出數字的標記底數。

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`，然後傳回*str*。

### <a name="example"></a>範例

如需如何使用 [ 的範例，請參閱 ](../standard-library/ios-functions.md#showbase)showbase`noshowbase`。

## <a name="noshowpoint"></a>noshowpoint

顯示小數部分為零之浮點數的整數部分。

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`noshowpoint` 預設為開啟；請使用 [showpoint](../standard-library/ios-functions.md#showpoint) 和 [precision](../standard-library/ios-base-class.md#precision) 來顯示小數點後的零。

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`，然後傳回*str*。

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

## <a name="noshowpos"></a>noshowpos

使正數不明確標示正負號。

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`noshowpos` 。

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`，然後傳回*str*。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/ios-functions.md#showpos)showpos`noshowpos`。

## <a name="noskipws"></a>noskipws

使輸入資料流讀取空格。

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[skipws](../standard-library/ios-functions.md#skipws) 預設為啟用。 在輸入資料流中讀取到空格時，即表示已達到緩衝區結尾。

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`，然後傳回*str*。

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

## <a name="nounitbuf"></a>nounitbuf

使輸出在緩衝區已滿時進行緩衝並繼續處理。

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[unitbuf](../standard-library/ios-functions.md#unitbuf) 會使得在緩衝區不為空時處理緩衝區。

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`，然後傳回*str*。

## <a name="nouppercase"></a>nouppercase

指定以小寫顯示十六進位數字和科學標記法中的指數。

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

操作工具會有效地呼叫 `str.`[unsetf](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`，然後傳回*str*。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/ios-functions.md#uppercase)uppercase`nouppercase`。

## <a name="oct"></a>月

指定以基底 8 標記法顯示整數變數。

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

整數變數預設會使用以 10 為底數的標記法來顯示。 [dec](../standard-library/ios-functions.md#dec) 和 [hex](../standard-library/ios-functions.md#hex) 也會變更整數變數的顯示方式。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`，然後傳回*str*。

### <a name="example"></a>範例

如需如何使用 `oct`的範例，請參閱[dec](../standard-library/ios-functions.md#dec) 。

## <a name="right"></a>再

使與輸出寬度不同寬的文字出現在具有右邊界的資料流排清中。

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[left](../standard-library/ios-functions.md#left) 也會修改文字的對齊方式。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`，然後傳回*str*。

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

## <a name="scientific"></a>記

讓浮點數以科學標記法顯示。

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[fixed](../standard-library/ios-functions.md#fixed) 標記法是浮點數的預設標記法。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`，然後傳回*str*。

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

## <a name="showbase"></a>showbase

指出據以顯示數字的標記基底。

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

數字的標示底數可以藉由 [dec](../standard-library/ios-functions.md#dec)、[oct](../standard-library/ios-functions.md#oct) 或 [hex](../standard-library/ios-functions.md#hex) 來變更。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`，然後傳回*str*。

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

## <a name="showpoint"></a>showpoint

顯示浮點數的整數部分和小數點右側的數字，即使小數部分為零亦然。

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[noshowpoint](../standard-library/ios-functions.md#noshowpoint) 預設為啟用。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`，然後傳回*str*。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/ios-functions.md#noshowpoint)noshowpoint`showpoint`。

## <a name="showpos"></a>showpos

使正數明確標示正負號。

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[noshowpos](../standard-library/ios-functions.md#noshowpos) 是預設值。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`，然後傳回*str*。

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

## <a name="skipws"></a>skipws

使輸入資料流不讀取空格。

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

`skipws` 預設為啟用。 [noskipws](../standard-library/ios-functions.md#noskipws) 會導致從輸入資料流讀取空格。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`，然後傳回*str*。

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

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a>unitbuf

使輸出在緩衝區不為空時進行處理。

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

請注意，`endl` 也會清除緩衝區。

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) 預設為啟用。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：： unitbuf](../standard-library/ios-base-class.md#fmtflags)`)`，然後傳回*str*。

## <a name="uppercase"></a>  uppercase

指定以大寫顯示十六進位數字和科學標記法中的指數。

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>參數

*str*\
對 [ios_base](../standard-library/ios-base-class.md) 類型之物件的參考，或對繼承自 `ios_base` 之類型的參考。

### <a name="return-value"></a>傳回值

衍生*str*之物件的參考。

### <a name="remarks"></a>備註

[nouppercase](../standard-library/ios-functions.md#nouppercase) 預設為啟用。

操作工具會有效地呼叫 `str.`[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：：大寫](../standard-library/ios-base-class.md#fmtflags)`)`，然後傳回*str*。

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
