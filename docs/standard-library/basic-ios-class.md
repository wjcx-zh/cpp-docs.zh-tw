---
title: basic_ios 類別
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: b730933879df04d2455b5eae6fc5abf16bbf4484
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219270"
---
# <a name="basic_ios-class"></a>basic_ios 類別

類別範本描述相依于樣板參數的輸入資料流程（屬於類別範本[basic_istream](../standard-library/basic-istream-class.md)）和輸出資料流程（屬於類別範本[basic_ostream](../standard-library/basic-ostream-class.md)）通用的儲存體和成員函式。 （類別[ios_base](../standard-library/ios-base-class.md)描述哪些是通用的，而不是相依于範本參數）。類別的物件**basic_ios \<class Elem, class Traits> **可協助控制具有類型之元素的資料流程 `Elem` ，其字元特性是由類別所決定 `Traits` 。

## <a name="syntax"></a>語法

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>參數

*Elem*\
類型。

*共同*\
類型為 `char_traits` 的變數。

## <a name="remarks"></a>備註

類別的物件**basic_ios \<class Elem, class Traits> **會儲存：

- Basic_istream 類型之物件的系結指標[basic_istream](../standard-library/basic-istream-class.md) **\<Elem, Traits>** 。

- [Basic_streambuf](../standard-library/basic-streambuf-class.md)類型之物件的資料流程緩衝區指標 **\<Elem, Traits >** 。

- [格式設定資訊](../standard-library/ios-base-class.md)。

- [ios_base](../standard-library/ios-base-class.md) 類型基底物件中的[資料流狀態資訊](../standard-library/ios-base-class.md)。

- `char_type` 類型物件中的填滿字元。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_ios](#basic_ios)|建構 `basic_ios` 類別。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|`Elem` 樣板參數的同義字。|
|[int_type](#int_type)|`Traits::int_type` 的同義字。|
|[off_type](#off_type)|`Traits::off_type` 的同義字。|
|[pos_type](#pos_type)|`Traits::pos_type` 的同義字。|
|[traits_type](#traits_type)|`Traits` 樣板參數的同義字。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[bad](#bad)|表示資料流緩衝區的完整性遺失。|
|[明確](#clear)|清除所有錯誤的旗標。|
|[copyfmt](#copyfmt)|將旗標從某個資料流複製到另一個資料流。|
|[eof](#eof)|表示是否已到達資料流的結尾。|
|[exceptions](#exceptions)|表示此資料流會擲回哪些例外狀況。|
|[無法](#fail)|表示無法從資料流擷取有效的欄位。|
|[填滿](#fill)|當此文字比該資料流還窄時，指定或傳回將要使用的字元。|
|[充分](#good)|表示資料流處於良好狀況。|
|[imbue](#imbue)|變更地區設定。|
|[init](#init)|由 `basic_ios` 建構函式所呼叫。|
|[move](#move)|將所有值從此參數移動至目前物件，但該資料流緩衝區的指標除外。|
|[narrow](#narrow)|尋找指定之 `char_type` 的對等字元。|
|[rdbuf](#rdbuf)|將資料流路由轉送到指定緩衝區。|
|[rdstate](#rdstate)|讀取旗標的位元狀態。|
|[set_rdbuf](#set_rdbuf)|指派此資料流緩衝區為此資料流物件的讀取緩衝區。|
|[setstate](#setstate)|設定其他旗標。|
|[調換](#swap)|用另一個 `basic_ios` 物件中的值交換這個 `basic_ios` 物件中的值。 不會交換資料流緩衝區的指標。|
|[tie](#tie)|可確保一個資料流在另一個資料流之前先處理。|
|[widen](#widen)|尋找指定字元的對等 `char_type`。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[explicit operator bool](#op_bool)|允許使用 `basic_ios` 物件做為 **`bool`** 。 自動類型轉換會停用，以避免常見非預期的副作用。|
|[operator void *](#op_void_star)|表示資料流是否仍然良好。|
|[操作!](#op_not)|表示資料流是否沒有錯誤。|

## <a name="requirements"></a>需求

**標頭：**\<ios>

**命名空間：** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios：：錯誤

表示資料流緩衝區的完整性遺失

```cpp
bool bad() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 `rdstate & badbit` 不是零，則為，否則為 **`false`** 。

如需 `badbit` 的詳細資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

### <a name="example"></a>範例

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios：： basic_ios

建構 basic_ios 類別。

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>參數

*sb*\
要儲存輸入或輸出元素的標準緩衝區。

### <a name="remarks"></a>備註

第一個建構函式會藉由呼叫 [init](#init)(_ *Sb*) 初始化其成員物件。 第二個 (受保護的) 建構函式會保留其成員物件的未初始化狀態。 稍後對的呼叫 `init` 必須先將物件初始化，才能安全地終結。

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios：： char_type

`Elem` 樣板參數的同義字。

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios：： clear

清除所有錯誤的旗標。

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>參數

*狀態*\
選擇性清除所有旗標之後要設定的旗標。 預設為 `goodbit`。

*reraise*\
選擇性指定是否應重新引發例外狀況。 預設值為 **`false`** （不會重新引發例外狀況）。

### <a name="remarks"></a>備註

旗標為 `goodbit` 、 `failbit` 、 `eofbit` 和 `badbit` 。 使用 [good](#good)、[bad](#bad)、[eof](#eof) 和 [fail](#fail) 測試這些旗標

成員函式會以下列項目取代預存的資料流狀態資訊：

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

如果 `state` **&** [例外](#exceptions)狀況為非零值，則會擲回類別[失敗](../standard-library/ios-base-class.md#failure)的物件。

### <a name="example"></a>範例

如需使用的範例，請參閱[rdstate](#rdstate)和[getline](../standard-library/string-functions.md#getline) `clear` 。

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios：： copyfmt

將旗標從某個資料流複製到另一個資料流。

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>參數

*再*\
您要複製其旗標的資料流。

### <a name="return-value"></a>傳回值

**`this`** 您要將旗標複製到其中之資料流程的物件。

### <a name="remarks"></a>備註

此成員函式會報告回呼事件**清除 \_ 事件**。 然後，它會*right*從右邊** \* 複製到填**滿字元、系結指標和格式資訊。 在改變例外狀況遮罩之前，它會報告回呼事件 `copyfmt_event` 。 如果複製完成之後，**state &**[exceptions](#exceptions) 為非零值，此函式會以引數 [rdstate](#rdstate) 有效呼叫 [clear](#clear)。 它會傳回** \* 此**。

### <a name="example"></a>範例

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios：： eof

表示是否已到達資料流的結尾。

```cpp
bool eof() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果已到達資料流程的結尾，則為， **`false`** 否則為。

### <a name="remarks"></a>備註

**`true`** 如果[rdstate](#rdstate) `& eofbit` 為非零值，則成員函式會傳回。 如需 `eofbit` 的詳細資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

### <a name="example"></a>範例

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios：：例外狀況

表示此資料流會擲回哪些例外狀況。

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>參數

*Newexcept*\
您要擲回例外狀況的旗標。

### <a name="return-value"></a>傳回值

目前指定要針對資料流擲回例外狀況的旗標。

### <a name="remarks"></a>備註

第一個成員函式會傳回預存的例外狀況遮罩。 第二個成員函式會在例外狀況遮罩中儲存 *_Except*，並傳回其先前儲存的值。 請注意，儲存新的例外狀況遮罩可能會擲回例外狀況，就像是呼叫 [clear](#clear)( [rdstate](#rdstate) ) 一樣。

### <a name="example"></a>範例

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios：： fail

表示無法從資料流擷取有效的欄位。

```cpp
bool fail() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果[rdstate](#rdstate) `& (badbit|failbit)` 為非零值，則為，否則為 **`false`** 。

如需 `failbit` 的詳細資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

### <a name="example"></a>範例

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios：： fill

當此文字比該資料流還窄時，指定或傳回將要使用的字元。

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>參數

*Char*\
您要當做填滿字元的字元。

### <a name="return-value"></a>傳回值

目前的填滿字元。

### <a name="remarks"></a>備註

第一個成員函式會傳回預存的填滿字元。 第二個成員函式會將*Char*儲存在填滿字元中，並傳回其先前儲存的值。

### <a name="example"></a>範例

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios：：好

表示資料流處於良好狀況。

```cpp
bool good() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果[rdstate](#rdstate) `== goodbit` （未設定狀態旗標），則為，否則為 **`false`** 。

如需 `goodbit` 的詳細資訊，請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)。

### <a name="example"></a>範例

如需 `good` 的使用範例，請參閱 [basic_ios:: bad](#bad)。

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios：： imbue

變更地區設定。

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>參數

*Loc*\
地區設定字串。

### <a name="return-value"></a>傳回值

先前的地區設定。

### <a name="remarks"></a>備註

如果 [rdbuf](#rdbuf) 不是 null 指標，此成員函式會呼叫

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

在任何情況下，它都會傳回 [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*)。

### <a name="example"></a>範例

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios：： init

由 basic_ios 建構函式呼叫。

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>參數

*_Sb*\
要儲存輸入或輸出元素的標準緩衝區。

*_Isstd*\
指定這是否為標準資料流。

### <a name="remarks"></a>備註

此成員函式會儲存所有成員物件中的值，因此：

- [rdbuf](#rdbuf) 會傳回 *_Sb*。

- [tie](#tie) 會傳回 null 指標。

- 如果 *_Sb*非零值， [rdstate](#rdstate)會傳回[goodbit](../standard-library/ios-base-class.md#iostate) ;否則，它會傳回[badbit](../standard-library/ios-base-class.md#iostate)。

- [例外](#exceptions)狀況傳回 `goodbit` 。

- [flags](../standard-library/ios-base-class.md#flags) 會傳回 [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags)。

- [width](../standard-library/ios-base-class.md#width) 會傳回 0。

- [precision](../standard-library/ios-base-class.md#precision) 會傳回 6。

- [fill](#fill) 會傳回空白字元。

- [getloc](../standard-library/ios-base-class.md#getloc) 會傳回 `locale::classic`。

- [iword](../standard-library/ios-base-class.md#iword) 會傳回零，而 [pword](../standard-library/ios-base-class.md#pword) 會針對所有引數值傳回 null 指標。

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios：： int_type

`traits_type::int_type` 的同義字。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios：： move

將所有值從此參數移動至目前物件，但該資料流緩衝區的指標除外。

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>參數

*再*\
要從中移動值的 `ios_base` 物件。

### <a name="remarks"></a>備註

受保護的成員函式會將儲存在*右方*的所有值移至以外的位置 **`*this`** ，但在中 `stream buffer pointer` ，不會變更，*而*是在中設定為 null 指標 **`*this`** 。 預存的 `tie pointer` 會設定為*右邊*的 null 指標。

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios：：窄

尋找指定之 `char_type` 的對等字元。

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>參數

*Char*\
**`char`** 要轉換的。

*預設*\
**`char`** 如果找不到對等的，您要傳回的。

### <a name="return-value"></a>傳回值

與指定的相等的 **`char`** `char_type` 。

### <a name="remarks"></a>備註

此成員函式會傳回[use_facet](../standard-library/basic-filebuf-class.md#open) \<ctype\<E> > （ [getloc](../standard-library/ios-base-class.md#getloc)（））。 `narrow`( `Char`, `Default`).

### <a name="example"></a>範例

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios：： off_type

`traits_type::off_type` 的同義字。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios：： operator void *

表示資料流是否仍然良好。

```cpp
operator void *() const;
```

### <a name="return-value"></a>傳回值

此運算子只有在 [fail](#fail) 時才會傳回 null 指標。

### <a name="example"></a>範例

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios：： operator！

表示資料流是否沒有錯誤。

```cpp
bool operator!() const;
```

### <a name="return-value"></a>傳回值

傳回 [fail](#fail)。

### <a name="example"></a>範例

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios：： operator bool

允許使用 `basic_ios` 物件做為 **`bool`** 。 自動類型轉換會停用，以避免常見非預期的副作用。

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>備註

只有在時，運算子才會傳回可轉換成的值 **`false`** `fail()` 。 傳回型別只能轉換成 **`bool`** ，而非 `void *` 或其他已知的純量型別。

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios：:p os_type

`traits_type::pos_type` 的同義字。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios：： rdbuf

將資料流路由轉送到指定緩衝區。

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>參數

*_Sb*\
資料流。

### <a name="remarks"></a>備註

第一個成員函式會傳回預存的資料流緩衝區指標。

第二個成員函式會將 *_Sb*儲存在儲存的資料流程緩衝區指標，並傳回先前儲存的值。

### <a name="example"></a>範例

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios：： rdstate

讀取旗標的位元狀態。

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>傳回值

預存的資料流狀態資訊。

### <a name="example"></a>範例

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios：： setstate

設定其他旗標。

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>參數

*_State*\
要設定的其他旗標。

### <a name="remarks"></a>備註

此成員函式會有效呼叫 [clear](#clear)(_ *State* &#124; [rdstate](#rdstate))。

### <a name="example"></a>範例

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios：： set_rdbuf

指派此資料流緩衝區為此資料流物件的讀取緩衝區。

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>參數

*strbuf*\
要成為讀取緩衝區的資料流緩衝區。

### <a name="remarks"></a>備註

受保護的成員函式會將*strbuf*儲存在中 `stream buffer pointer` 。它不會呼叫 `clear` 。

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios：：系結

可確保一個資料流在另一個資料流之前先處理。

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>參數

*str*\
資料流。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回預存的繫結指標。 第二個成員函式會將*str*儲存在系結指標中，並傳回其先前儲存的值。

### <a name="remarks"></a>備註

`tie` 會使兩個資料流同步；因此，當其中一個資料流的作業完成之後，就會進行另一個資料流的作業。

### <a name="example"></a>範例

在此範例中，將 cin 繫結至 cout 可確保 "Enter a number:" 字串會先移至主控台，再從 cin 中擷取數字本身。 這樣做可避免在讀取數字時，"Enter a number:" 字串仍在緩衝區中的可能性，因此我們可以確定使用者實際上會有可做出回應的一些提示。 根據預設，cin 會與 cout 繫結。

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios：： traits_type

`Traits` 樣板參數的同義字。

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios：：加寬

尋找與指定的相等的 `char_type` **`char`** 。

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>參數

*Char*\
要轉換的字元。

### <a name="return-value"></a>傳回值

尋找與指定的相等的 `char_type` **`char`** 。

### <a name="remarks"></a>備註

此成員函式會傳回[use_facet](../standard-library/basic-filebuf-class.md#open) <  **ctype** \< **E**> > （ [getloc](../standard-library/ios-base-class.md#getloc)）。 `widen`( `Char`).

### <a name="example"></a>範例

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios：： swap

用另一個 `basic_ios` 物件中的值交換這個 `basic_ios` 物件中的值。 但不交換資料流緩衝區的指標。

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>參數

*再*\
用來交換值的 `basic_ios` 物件。

### <a name="remarks"></a>備註

受保護的成員函式會交換*儲存在中*的所有值， **`*this`** 但儲存的除外 `stream buffer pointer` 。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
