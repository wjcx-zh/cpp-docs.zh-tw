---
title: basic_istream 類別
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: da53db594e057449f2d227f57c902d26396000b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219244"
---
# <a name="basic_istream-class"></a>basic_istream 類別

描述一個物件，該物件可控制如何從具有 `Char_T` 類型 (也稱為 [char_type](../standard-library/basic-ios-class.md#char_type)) 之元素的資料流緩衝區擷取元素和編碼物件；其中該類型的字元特性是由 *Tr* 類別 (也稱為 [traits_type](../standard-library/basic-ios-class.md#traits_type)) 所決定。

## <a name="syntax"></a>語法

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_istream : virtual public basic_ios<Char_T, Tr>
```

## <a name="remarks"></a>備註

大部分多載 [operator>>](#op_gt_gt) 的成員函式為格式化的輸入函式。 它們遵循下列模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

許多其他的成員函式為未經格式化的輸入函式。 它們遵循下列模式：

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

如果兩個函式群組在 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(eofbit)` 解壓縮專案時遇到檔案結尾，則會呼叫。

類別的物件存放 `basic_istream<Char_T, Tr>` 區：

- 類別的虛擬公用基底物件 [`basic_ios`](../standard-library/basic-ios-class.md) `<Char_T, Tr>` 。

- 上次未格式化輸入作業的提取計數（ `count` 在先前的程式碼中呼叫）。

## <a name="example"></a>範例

若要深入了解輸入資料流，請參閱 [basic_ofstream 類別](../standard-library/basic-ifstream-class.md)的範例。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_istream](#basic_istream)|建構類型 `basic_istream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[gcount](#gcount)|傳回最後一個未經格式化的輸入期間，讀取的字元數。|
|[get](#get)|從輸入資料流讀取一或多個字元。|
|[getline](#getline)|從輸入資料流讀取一行。|
|[ignore](#ignore)|導致從目前的讀取位置略過一些項目。|
|[查看](#peek)|傳回要讀取的下一個字元。|
|[putback](#putback)|將指定的字元放入資料流。|
|[閱讀文章](#read)|從資料流讀取指定的字元數，並將其儲存在陣列中。|
|[readsome](#readsome)|只從緩衝區讀取。|
|[seekg](#seekg)|移動資料流中的讀取位置。|
|[sentry](#sentry)|此巢狀類別會描述物件，該物件的宣告會建構格式化的輸入函式以及未經格式化的輸入函式。|
|[調換](#swap)|以 `basic_istream` 物件交換所提供的 `basic_istream` 物件參數。|
|[保持](#sync)|同步處理資料流程的相關輸入裝置與資料流程的緩衝區。|
|[tellg](#tellg)|回報在資料流中目前的讀取位置。|
|[unget](#unget)|將最近讀取的字元放回資料流。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[運算子>>](#op_gt_gt)|呼叫輸入資料流上的函式，或從輸入資料流讀取經格式化的資料。|
|[operator =](#op_eq)|將位於運算子右側的 `basic_istream` 指派給此物件。 這是一個移動指派，涉及 `rvalue` 不會留下複本的參考。|

## <a name="requirements"></a>需求

**標頭：**\<istream>

**命名空間：** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream：： basic_istream

建構類型 `basic_istream` 的物件。

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>參數

*strbuf*\
[basic_streambuf](../standard-library/basic-streambuf-class.md) 類型的物件。

*_Isstd*\
**`true`** 如果是標準資料流程，則為，否則為 **`false`** 。

*再*\
要複製的 `basic_istream` 物件。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫來初始化基類 [`init`](../standard-library/basic-ios-class.md#init) `(strbuf)` 。 它也會在擷取計數中儲存零。 如需此提取計數的詳細資訊，請參閱[Basic_istream 類別](../standard-library/basic-istream-class.md)總覽的「備註」一節。

第二個建構函式會藉由呼叫 `move(right)` 初始化基底類別。 它也會儲存 `right.gcount()` 在提取計數中，並在 * right * * 的提取計數中儲存零。

### <a name="example"></a>範例

若要深入了解輸入資料流，請參閱 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) 的範例。

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream：： gcount

傳回最後一個未經格式化的輸入期間，讀取的字元數。

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>傳回值

擷取計數。

### <a name="remarks"></a>備註

請使用 [basic_istream:: get](#get) 來讀取未格式化的字元。

### <a name="example"></a>範例

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream：： get

從輸入資料流讀取一或多個字元。

```cpp
int_type get();

basic_istream<Char_T, Tr>& get(Char_T& Ch);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count);
basic_istream<Char_T, Tr>& get(Char_T* str, streamsize count, Char_T delimiter);

basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf);
basic_istream<Char_T, Tr>& get(basic_streambuf<Char_T, Tr>& strbuf, Char_T delimiter);
```

### <a name="parameters"></a>參數

*計數*\
要從 *strbuf* 中讀取的字元數。

*為止*\
如果在*count*之前遇到，則應終止讀取的字元。

*str*\
要在其中寫入的字串。

*頻道*\
要取得的字元。

*strbuf*\
要在其中寫入的緩衝區。

### <a name="return-value"></a>傳回值

無參數格式的 get 會將讀取的元素當做整數或檔案結尾傳回。 其餘的表單會傳回資料流程（* **`this`** ）。

### <a name="remarks"></a>備註

第一個未格式化的輸入函式會盡可能地解壓縮專案，就像是藉由傳回一樣 `rdbuf->sbumpc` 。 否則，它會傳回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 。 如果函式未解壓縮任何元素，則會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。

第二個函式會以相同方式來擷取 [int_type](../standard-library/basic-ios-class.md#int_type) 元素 `meta`。 如果 `meta` 比較等於 `traits_type::eof` ，則函數會呼叫 `setstate(failbit)` 。 否則，它會儲存 `traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(meta)` 在*Ch*中。 函式會傳回 __* this__。

第三個函式會傳回 `get(str, count, widen('\n'))` 。

第四個函式會解壓縮到個 `count - 1` 元素，並將它們儲存在以*str*開頭的陣列中。 它一律會在所儲存的任何已擷取元素之後儲存 `char_type`。 為了進行測試，在下列情況下會停止擷取：

- 到達檔案結尾時。

- 函式之後，會將比較等於*分隔符號*的元素解壓縮。 在此情況下，元素會放回受控制的序列。

- 函式解壓縮專案之後 `count - 1` 。

如果此函式未擷取任何元素，則會呼叫 `setstate(failbit)`. 在任何情況下，它會傳回 __* this__。

第五個函式會傳回 `get(strbuf, widen('\n'))` 。

第六個函式會擷取元素並將其插入 *strbuf*。 在檔案結尾或比較等於*分隔符號*（不會解壓縮）的元素上停用解壓縮。 如果插入失敗或擲回例外狀況 (會攔截但不會再次擲回)，也會停止，而不會擷取有問題的元素。 如果此函式未擷取任何元素，則會呼叫 `setstate(failbit)`. 在任何情況下，函數都會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream：： getline

從輸入資料流取得一行。

```cpp
basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Char_T, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type delimiter);
```

### <a name="parameters"></a>參數

*計數*\
要從 *strbuf* 中讀取的字元數。

*為止*\
如果在*count*之前遇到，則應終止讀取的字元。

*str*\
要在其中寫入的字串。

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

這些未格式化輸入函數的第一個會傳回 `getline(str, count, widen('\n'))` 。

第二個函式會解壓縮到個 `count - 1` 元素，並將它們儲存在以*str*開頭的陣列中。 它一律會在所儲存的任何已擷取元素之後儲存字串結束字元。 為了進行測試，在下列情況下會停止擷取：

- 到達檔案結尾時。

- 函式之後，會將比較等於*分隔符號*的元素解壓縮。 在此情況下，不會將元素放回，而且不會附加至受控制的序列。

- 函式解壓縮專案之後 `count - 1` 。

如果函式未解壓縮任何元素或專案 `count - 1` ，則會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情況下，它會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream：： ignore

導致從目前的讀取位置略過一些項目。

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>參數

*計數*\
要從目前的讀取位置略過的元素數目。

*為止*\
元素，如果在 count 之前遇到，會導致傳回， `ignore` 並允許讀取*分隔符號*之後的所有專案。

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

未格式化的輸入函式會解壓縮以*計算*元素並予以捨棄。 不過，如果*count*等於 `numeric_limits<int>::max` ，則會被視為任意大小。 在檔案結尾或元素（ `Ch` `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(Ch)` 也就是也會解壓縮的）上進行*delimiter*解壓縮時，會提早停止。 函式會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>基本 \_ istream：： operator>>

呼叫輸入資料流上的函式，或從輸入資料流讀取經格式化的資料。

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Char_T, Tr>& (* Pfn)(basic_ios<Char_T, Tr>&));
basic_istream& operator>>(basic_streambuf<Char_T, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>參數

*Pfn*\
函式指標。

*strbuf*\
`stream_buf` 類型的物件。

*初始值*\
要從資料流中讀取的值。

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

\<istream> 標頭也會定義數個全域擷取運算子。 如需詳細資訊，請參閱[operator>>  （ \<istream> ）](../standard-library/istream-operators.md#op_gt_gt)。

第一個成員函式可確保表單的運算式會 `istr >> ws` 呼叫，然後傳回 [`ws`](../standard-library/istream-functions.md#ws) `(istr)` __* this__。 第二個和第三個函式可確保其他操作工具（例如 [`hex`](../standard-library/ios-functions.md#hex) ）的行為類似。 其餘的函式為格式化的輸入函式。

函式：

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

如果*strbuf*不是 null 指標，則會將元素解壓縮，並將它們插入*strbuf*中。 到達檔案結尾時，會停止擷取。 如果插入失敗或擲回例外狀況 (會攔截但不會再次擲回)，也會停止，而不會擷取有問題的元素。 如果函式未解壓縮任何元素，則會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情況下，函數都會傳回 __* this__。

函式：

```cpp
basic_istream& operator>>(bool& val);
```

藉由呼叫來解壓縮欄位，並將它轉換成布林值 [`use_facet`](../standard-library/basic-filebuf-class.md#open) `< num_get<Char_T, InIt>(` [`getloc`](../standard-library/ios-base-class.md#getloc) `).` [`get`](../standard-library/ios-base-class.md#getloc) `( InIt(` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `), Init(0), *this, getloc, val)` 。 在這裡， `InIt` 會定義為 [`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md) `<Char_T, Tr>` 。 函式會傳回 __* this__。

每個函數：

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

藉由呼叫來解壓縮欄位，並將它轉換為數值 `use_facet<num_get<Char_T, InIt>(getloc).` [`get`](#get) `(InIt(rdbuf), Init(0), *this, getloc, val)` 。 這裡的 `InIt` 定義為 `istreambuf_iterator<Char_T, Tr>` ，而*val*則具有類型 **`long`** 、 **`unsigned long`** 或（ **`void`** <strong>\*</strong> 如有需要）。

如果轉換的值無法表示為*val*的類型，則函數會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情況下，函數都會傳回 __* this__。

每個函數：

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

藉由呼叫來解壓縮欄位，並將它轉換為數值 `use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)` 。 在這裡， `InIt` 定義為 `istreambuf_iterator<Char_T, Tr>` ，而*val*具有類型 **`double`** 或 **`long double`** （視需要）。

如果轉換的值無法表示為*val*的類型，則函數會呼叫 `setstate(failbit)` 。 在任何情況下，它會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream：： operator =

將位於運算子右側的 `basic_istream` 指派給此物件。 這是一個移動指派，涉及 `rvalue` 不會留下複本的參考。

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_ifstream` 物件的 `rvalue` 參考。

### <a name="return-value"></a>傳回值

傳回 __* this__。

### <a name="remarks"></a>備註

成員運算子會呼叫 `swap(right)` 。

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream：:p eek

傳回要讀取的下一個字元。

```cpp
int_type peek();
```

### <a name="return-value"></a>傳回值

要讀取的下一個字元。

### <a name="remarks"></a>備註

未格式化的輸入函式會盡可能地解壓縮專案，就像是藉由傳回一樣 `rdbuf->` [`sgetc`](../standard-library/basic-streambuf-class.md#sgetc) 。 否則，它會傳回 `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) 。

### <a name="example"></a>範例

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream：:p utback

將指定的字元放入資料流。

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>參數

*頻道*\
要放回資料流的字元。

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

未[格式化的輸入](../standard-library/basic-istream-class.md)函式會盡可能放回*Ch*，如同藉由呼叫一樣 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc) 。 如果 `rdbuf` 是 null 指標，或如果的呼叫傳回 `sputbackc` `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof) ，則函數會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 。 在任何情況下，它會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream：： read

從資料流讀取指定的字元數，並將其儲存在陣列中。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>參數

*str*\
要讀取其中字元的陣列。

*計數*\
要讀取的字元數。

### <a name="return-value"></a>傳回值

資料流程（ **`*this`** ）。

### <a name="remarks"></a>備註

未格式化的輸入函式會解壓縮以*計算*元素，並將它們儲存在以*str*開頭的陣列中。 解壓縮會在檔案結尾停止，在這種情況下，函數會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情況下，它會傳回 __* this__。

### <a name="example"></a>範例

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream：： readsome

讀取指定數目的字元值。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>參數

*str*\
`readsome` 要在其中儲存所讀取字元的陣列。

*計數*\
要讀取的字元數。

### <a name="return-value"></a>傳回值

實際讀取的字元數， [`gcount`](#gcount) 。

### <a name="remarks"></a>備註

這個未格式化的輸入函式會將輸入資料流程中的專案*數*解壓縮，並將它們儲存在陣列*str*中。

此函式不會等候輸入。 它會讀取任何可用的資料。

### <a name="example"></a>範例

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream：： seekg

移動資料流中的讀取位置。

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>參數

*採購*\
要在其中移動讀取指標的絕對位置。

*停止*\
相對於*方式*移動讀取指標的位移。

*方式*\
其中一個 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 列舉。

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

第一個成員函式會執行絕對搜尋，第二個成員函式會執行相對搜尋。

> [!NOTE]
> 請勿對文字檔案使用第二個成員函式，因為標準 C++ 不支援在文字檔案中執行相對搜尋。

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 為 false，則第一個成員函式會呼叫 `newpos =` [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos) `(pos)` 某個 `pos_type` 暫存物件的 `newpos` 。 如果 `fail` 為 false，則第二個函數會呼叫 `newpos = rdbuf->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `( off, way)` 。 不論是哪一種情況，如果 `(off_type)newpos == (off_type)(-1)` （定位作業失敗），函數都會呼叫 `istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 這兩個函數都會傳回 __* this__。

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 為 true，則成員函式不會執行任何動作。

### <a name="example"></a>範例

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream：： sentry

此巢狀類別描述一個物件，該物件的宣告會建構格式化和未格式化的輸入函式。

```cpp
class sentry {
   public:
   explicit sentry(
      basic_istream<Char_T, Tr>& _Istr,
      bool _Noskip = false);
   operator bool() const;
   };
```

### <a name="remarks"></a>備註

如果 `_Istr.` [`good`](../standard-library/basic-ios-class.md#good) 為 true，則表示函式：

- `_Istr.` [`tie`](../standard-library/basic-ios-class.md#tie) `->` [`flush`](../standard-library/basic-ostream-class.md#flush) 如果不 `_Istr.tie` 是 null 指標，則會呼叫。

- [`ws`](../standard-library/istream-functions.md#ws) `(_Istr)` 如果 `_Istr.` [`flags`](../standard-library/ios-base-class.md#flags) `&` [`skipws`](../standard-library/ios-functions.md#skipws) 為非零值，則有效地呼叫。

如果在任何這類準備之後， `_Istr.good` 為 false，則此函式會呼叫 `_Istr.` [`setstate`](../standard-library/basic-ios-class.md#setstate) `(failbit)` 。 在任何情況下，此函式會將所傳回的值儲存 `_Istr.good` 在中 `status` 。 稍後的呼叫會 `operator bool` 傳遞此儲存值。

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream：： swap

交換兩個 `basic_istream` 物件的內容。

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_istream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

此成員函式會呼叫 [`basic_ios::swap`](../standard-library/basic-ios-class.md#swap) `(right)` 。 它也會以*右邊*的提取計數來交換提取計數。

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream：： sync

同步處理資料流程的相關輸入裝置與資料流程的緩衝區。

```cpp
int sync();
```

### <a name="return-value"></a>傳回值

如果 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) 是 null 指標，此函式會傳回-1。 否則，它會呼叫 `rdbuf->` [`pubsync`](../standard-library/basic-streambuf-class.md#pubsync) 。 如果該呼叫傳回-1，則函式會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 並傳回-1。 否則，此函式會傳回零。

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream：： tellg

回報在資料流中目前的讀取位置。

```cpp
pos_type tellg();
```

### <a name="return-value"></a>傳回值

在資料流中的目前位置。

### <a name="remarks"></a>備註

如果 [`fail`](../standard-library/basic-ios-class.md#fail) 為 false，則成員函式會傳回 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) `->` [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) `(0, cur, in)` 。 否則會傳回 `pos_type(-1)`。

### <a name="example"></a>範例

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream：： unget

將最近讀取的字元放回資料流。

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>傳回值

資料流程（__* this__）。

### <a name="remarks"></a>備註

未[格式化的輸入](../standard-library/basic-istream-class.md)函式會在可能的情況下，將先前的元素放回資料流程中，如同呼叫一樣 `rdbuf->` [`sungetc`](../standard-library/basic-streambuf-class.md#sungetc) 。 如果 [`rdbuf`](../standard-library/basic-ios-class.md#rdbuf) 是 null 指標，或如果的呼叫傳回 `sungetc` `traits_type::` [`eof`](../standard-library/basic-ios-class.md#eof) ，則函數會呼叫 [`setstate`](../standard-library/basic-ios-class.md#setstate) `(badbit)` 。 在任何情況下，它會傳回 __* this__。

如需可能失敗的詳細資訊 `unget` ，請參閱 [`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc) 。

### <a name="example"></a>範例

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
