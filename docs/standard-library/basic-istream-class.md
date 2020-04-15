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
ms.openlocfilehash: 03a6e3a65d6dc8c2fa896949855bd23a01578e5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376832"
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

如果兩組函數在[`setstate`](../standard-library/basic-ios-class.md#setstate)`(eofbit)`提取元素時遇到檔結尾,則調用它們。

類別`basic_istream<Char_T, Tr>`儲存的物件:

- 類[`basic_ios`](../standard-library/basic-ios-class.md)`<Char_T, Tr>`的虛擬公共基礎物件。

- 最後一個未格式化的輸入操作(在前一代碼中`count`調用)的提取計數。

## <a name="example"></a>範例

若要深入了解輸入資料流，請參閱 [basic_ofstream 類別](../standard-library/basic-ifstream-class.md)的範例。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_istream](#basic_istream)|建構類型 `basic_istream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[gcount](#gcount)|傳回最後一個未經格式化的輸入期間，讀取的字元數。|
|[get](#get)|從輸入資料流讀取一或多個字元。|
|[getline](#getline)|從輸入資料流讀取一行。|
|[忽略](#ignore)|導致從目前的讀取位置略過一些項目。|
|[偷看](#peek)|傳回要讀取的下一個字元。|
|[putback](#putback)|將指定的字元放入資料流。|
|[讀](#read)|從資料流讀取指定的字元數，並將其儲存在陣列中。|
|[readsome](#readsome)|只從緩衝區讀取。|
|[seekg](#seekg)|移動資料流中的讀取位置。|
|[sentry](#sentry)|此巢狀類別會描述物件，該物件的宣告會建構格式化的輸入函式以及未經格式化的輸入函式。|
|[交換](#swap)|以 `basic_istream` 物件交換所提供的 `basic_istream` 物件參數。|
|[sync](#sync)|將流的關聯輸入設備與流的緩衝區同步。|
|[tellg](#tellg)|回報在資料流中目前的讀取位置。|
|[unget](#unget)|將最近讀取的字元放回資料流。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子>>](#op_gt_gt)|呼叫輸入資料流上的函式，或從輸入資料流讀取經格式化的資料。|
|[運算子*](#op_eq)|將位於運算子右側的 `basic_istream` 指派給此物件。 這是一個移動分配,涉及不`rvalue`留下副本的引用。|

## <a name="requirements"></a>需求

**標頭︰** \<istream>

**命名空間：** std

## <a name="basic_istreambasic_istream"></a><a name="basic_istream"></a>basic_istream:basic_istream

建構類型 `basic_istream` 的物件。

```cpp
explicit basic_istream(
    basic_streambuf<Char_T, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>參數

*斯特布夫*\
[basic_streambuf](../standard-library/basic-streambuf-class.md) 類型的物件。

*_Isstd*\
如果它是標準流,**則為 true;** 否則,**假**。

*對*\
要複製的 `basic_istream` 物件。

### <a name="remarks"></a>備註

第一個構造函數通過調用[`init`](../standard-library/basic-ios-class.md#init)`(strbuf)`初始化基類。 它也會在擷取計數中儲存零。 有關此提取計數的詳細資訊,請參閱[basic_istream類](../standard-library/basic-istream-class.md)概述的備註部分。

第二個建構函式會藉由呼叫 `move(right)` 初始化基底類別。 它還存儲在`right.gcount()`提取計數中,並將零存儲在 [右]的提取計數中。

### <a name="example"></a>範例

若要深入了解輸入資料流，請參閱 [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream) 的範例。

## <a name="basic_istreamgcount"></a><a name="gcount"></a>basic_istream:克數

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

## <a name="basic_istreamget"></a><a name="get"></a>basic_istream:取得

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

*分隔符*\
應在*計數*之前遇到應終止讀取的字元。

*Str*\
要在其中寫入的字串。

*Ch*\
要取得的字元。

*斯特布夫*\
要在其中寫入的緩衝區。

### <a name="return-value"></a>傳回值

無參數格式的 get 會將讀取的元素當做整數或檔案結尾傳回。 其餘格式會傳回資料流 (* `this`)。

### <a name="remarks"></a>備註

第一個未格式化的輸入函數提取一個元素(如果可能,就像返回`rdbuf->sbumpc`一樣)。 否則,它將返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)。 如果函數不提取任何元素,它將呼叫[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。

第二個函式會以相同方式來擷取 [int_type](../standard-library/basic-ios-class.md#int_type) 元素 `meta`。 如果`meta`比較等於`traits_type::eof`, 函數`setstate(failbit)`呼叫 。 否則,它儲存在`traits_type::`[`to_char_type`](../standard-library/char-traits-struct.md#to_char_type)`(meta)`*Ch*。 函數傳回 ___this__。

第三個函數`get(str, count, widen('\n'))`傳回 。

第四個函數提取到`count - 1`元素,並將它們存儲在從*str*開始的陣列中。 它一律會在所儲存的任何已擷取元素之後儲存 `char_type`。 為了進行測試，在下列情況下會停止擷取：

- 到達檔案結尾時。

- 函數提取一個與*分隔符*相等的元素。 在這種情況下,元素將放回受控序列。

- 函數提取`count - 1`元素后。

如果此函式未擷取任何元素，則會呼叫 `setstate(failbit)`. 在任何情況下,它傳回 ___this__。

第五個函數`get(strbuf, widen('\n'))`傳回 。

第六個函式會擷取元素並將其插入 *strbuf*。 提取停止在檔案結尾或元素上,該元素比較等於*分隔符*,不提取。 如果插入失敗或擲回例外狀況 (會攔截但不會再次擲回)，也會停止，而不會擷取有問題的元素。 如果此函式未擷取任何元素，則會呼叫 `setstate(failbit)`. 在任何情況下,函數傳回 ___this__。

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

## <a name="basic_istreamgetline"></a><a name="getline"></a>basic_istream:取得線

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

*分隔符*\
應在*計數*之前遇到應終止讀取的字元。

*Str*\
要在其中寫入的字串。

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

這些未格式化的輸入函數中的第一個`getline(str, count, widen('\n'))`傳回 。

第二個函數提取到`count - 1`元素,並將它們存儲在從*str*開始的陣列中。 它一律會在所儲存的任何已擷取元素之後儲存字串結束字元。 為了進行測試，在下列情況下會停止擷取：

- 到達檔案結尾時。

- 函數提取一個與*分隔符*相等的元素。 在這種情況下,元素不會放回,也不會追加到受控序列中。

- 函數提取`count - 1`元素后。

如果函數不提取任何元素或`count - 1`元素,它將呼[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`叫 。 在任何情況下,它傳回 ___this__。

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

## <a name="basic_istreamignore"></a><a name="ignore"></a>basic_istream:忽略

導致從目前的讀取位置略過一些項目。

```cpp
basic_istream<Char_T, Tr>& ignore(
    streamsize count = 1,
    int_type delimiter = traits_type::eof());
```

### <a name="parameters"></a>參數

*計數*\
要從目前的讀取位置略過的元素數目。

*分隔符*\
在計數之前遇到的元素會導致`ignore`返回,並允許在*分隔符*之後讀取所有元素。

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

未格式化的輸入函數將提取以對元素*進行計數*並丟棄它們。 但是*count*,如果計`numeric_limits<int>::max`數 等於,則視為任意大。 提取在檔案末尾`Ch`或元素上早期停止`traits_type::`[`to_int_type`](../standard-library/char-traits-struct.md#to_int_type)`(Ch)`, 以便與*分隔符*(也提取)進行比較。 函數傳回 ___this__。

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

## <a name="basic_istreamoperator"></a><a name="op_gt_gt"></a>基本\_istream::操作員>>

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

*普芬*\
函式指標。

*斯特布夫*\
`stream_buf` 類型的物件。

*瓦爾*\
要從資料流中讀取的值。

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

\<istream>标头还定义了多个全局提取运算符。 如需詳細資訊，請參閱 [operator>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt)。

第一`istr >> ws`個成員函數確保表單的表示式呼叫[`ws`](../standard-library/istream-functions.md#ws)`(istr)`,然後傳回 ___this__。 第二個和第三個函數可確保其他操縱器(如[`hex`](../standard-library/ios-functions.md#hex))的行為類似。 其餘函數是格式化的輸入函數。

函式：

```cpp
basic_istream& operator>>(
    basic_streambuf<Char_T, Tr>* strbuf);
```

提取元素,如果*strbuf*不是空指標,並在*strbuf*中插入它們。 到達檔案結尾時，會停止擷取。 如果插入失敗或擲回例外狀況 (會攔截但不會再次擲回)，也會停止，而不會擷取有問題的元素。 如果函數不提取任何元素,它將呼叫[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`。 在任何情況下,函數傳回 ___this__。

函式：

```cpp
basic_istream& operator>>(bool& val);
```

[`use_facet`](../standard-library/basic-filebuf-class.md#open)`< num_get<Char_T, InIt>(`提取[`get`](../standard-library/ios-base-class.md#getloc)`( InIt(`[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)欄位並透過調用將其轉換為布林`), Init(0), *this, getloc, val)`[`getloc`](../standard-library/ios-base-class.md#getloc)`).`值。 這裡定義為`InIt`[`istreambuf_iterator`](../standard-library/istreambuf-iterator-class.md)`<Char_T, Tr>`。 函數傳回 ___this__。

每個功能:

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

提取欄位,並通過調用`use_facet<num_get<Char_T, InIt>(getloc).`[`get`](#get)`(InIt(rdbuf), Init(0), *this, getloc, val)`將其轉換為數值。 此處,`InIt`定義`istreambuf_iterator<Char_T, Tr>`為 *,val*具有**長**、**無符號長**或**根據需要 void**<strong>\*</strong>的類型。

如果轉換的值不能表示為*val*類型,則函數將[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`呼叫 。 在任何情況下,函數傳回 ___this__。

每個功能:

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

提取欄位,並通過調用`use_facet<num_get<Char_T, InIt>(getloc).get(InIt(rdbuf), Init(0), *this, getloc, val)`將其轉換為數值。 此處,`InIt`定義`istreambuf_iterator<Char_T, Tr>`為 *,val*根據需要具有**雙**精度或**長雙精度。**

如果轉換的值不能表示為*val*類型,則函數將`setstate(failbit)`呼叫 。 在任何情況下,它傳回 ___this__。

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

## <a name="basic_istreamoperator"></a><a name="op_eq"></a>basic_istream::操作員*

將位於運算子右側的 `basic_istream` 指派給此物件。 這是一個移動分配,涉及不`rvalue`留下副本的引用。

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_ifstream` 物件的 `rvalue` 參考。

### <a name="return-value"></a>傳回值

返回 ___this__。

### <a name="remarks"></a>備註

成員運算子呼叫`swap(right)`。

## <a name="basic_istreampeek"></a><a name="peek"></a>basic_istream::p耶克

傳回要讀取的下一個字元。

```cpp
int_type peek();
```

### <a name="return-value"></a>傳回值

要讀取的下一個字元。

### <a name="remarks"></a>備註

如果可能,未格式化的輸入函數將提取一個元素,就像返回`rdbuf->`[`sgetc`](../standard-library/basic-streambuf-class.md#sgetc)一樣。 否則,它將返回`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)。

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

## <a name="basic_istreamputback"></a><a name="putback"></a>basic_istream::p

將指定的字元放入資料流。

```cpp
basic_istream<Char_T, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>參數

*Ch*\
要放回資料流的字元。

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

[未格式化的輸入函數](../standard-library/basic-istream-class.md)將*Ch(* 如果可能)放回,[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`sputbackc`](../standard-library/basic-streambuf-class.md#sputbackc)就像調用 一樣。 如果`rdbuf`為空指標,或者`sputbackc`對的呼叫,`traits_type::`[`eof`](../standard-library/char-traits-struct.md#eof)則函數將[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`呼叫 。 在任何情況下,它傳回 ___this__。

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

## <a name="basic_istreamread"></a><a name="read"></a>basic_istream::閱讀

從資料流讀取指定的字元數，並將其儲存在陣列中。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
basic_istream<Char_T, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>參數

*Str*\
要讀取其中字元的陣列。

*計數*\
要讀取的字元數。

### <a name="return-value"></a>傳回值

資料流 ( `*this`)。

### <a name="remarks"></a>備註

未格式化的輸入函數提取到*對元素進行計數*,並將它們存儲在從*str*開始的陣列中。 擷取在檔案末尾早期停止,在這種情況下函數呼[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`叫 。 在任何情況下,它傳回 ___this__。

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

## <a name="basic_istreamreadsome"></a><a name="readsome"></a>basic_istream::閱讀

讀取指定數目的字元值。

此方法有賴於呼叫者檢查傳遞的值是否正確，因此可能不安全。

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>參數

*Str*\
`readsome` 要在其中儲存所讀取字元的陣列。

*計數*\
要讀取的字元數。

### <a name="return-value"></a>傳回值

實際讀取的字元數[`gcount`](#gcount)。

### <a name="remarks"></a>備註

此未格式化的輸入函數提取起來,從輸入流*中計算*元素並將其存儲在陣列*str*中。

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

## <a name="basic_istreamseekg"></a><a name="seekg"></a>basic_istream:seekg

移動資料流中的讀取位置。

```cpp
basic_istream<Char_T, Tr>& seekg(pos_type pos);

basic_istream<Char_T, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>參數

*Pos*\
要在其中移動讀取指標的絕對位置。

*關閉*\
用於相對於方式移動讀取指標*的*偏移量。

*方式*\
其中一個 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 列舉。

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

第一個成員函式會執行絕對搜尋，第二個成員函式會執行相對搜尋。

> [!NOTE]
> 請勿對文字檔案使用第二個成員函式，因為標準 C++ 不支援在文字檔案中執行相對搜尋。

如果[`fail`](../standard-library/basic-ios-class.md#fail)為 false,則第一個`newpos =`[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)`(pos)`成員 函數將`pos_type`呼叫`newpos`,用於某些臨時物件 。 如果`fail`為 false,則`newpos = rdbuf->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`( off, way)`第二個函數呼叫 。 在這兩種情況下,如果`(off_type)newpos == (off_type)(-1)`(定位操作失敗),則函數呼`istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`叫 。 兩個函數傳回 ___this__。

如果[`fail`](../standard-library/basic-ios-class.md#fail)為 true,則成員函數不執行任何操作。

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

## <a name="basic_istreamsentry"></a><a name="sentry"></a>basic_istream:哨兵

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

如果`_Istr.`[`good`](../standard-library/basic-ios-class.md#good)為 true,則建構函數:

- `_Istr.`[`tie`](../standard-library/basic-ios-class.md#tie)如果`_Istr.tie`不是空指標,則調用。 `->` [`flush`](../standard-library/basic-ostream-class.md#flush)

- 有效呼叫[`ws`](../standard-library/istream-functions.md#ws)`(_Istr)``_Istr.`[`flags`](../standard-library/ios-base-class.md#flags)`&`([`skipws`](../standard-library/ios-functions.md#skipws)如果為非零)。

如果經過任何此類準備後,`_Istr.good`為 false,則建構`_Istr.`[`setstate`](../standard-library/basic-ios-class.md#setstate)`(failbit)`函數 呼叫 。 在任何情況下,構造函數都存儲`_Istr.good`在`status`中返回的值。 稍後調用以`operator bool`傳遞此存儲值。

## <a name="basic_istreamswap"></a><a name="swap"></a>basic_istream:交換

交換兩個 `basic_istream` 物件的內容。

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_istream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

成員函數呼叫[`basic_ios::swap`](../standard-library/basic-ios-class.md#swap)`(right)`。 它還將提取計數與*右*的提取計數交換。

## <a name="basic_istreamsync"></a><a name="sync"></a>basic_istream:同步

將流的關聯輸入設備與流的緩衝區同步。

```cpp
int sync();
```

### <a name="return-value"></a>傳回值

如果[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)為空指標,則函數返回 -1。 否則,它將呼叫`rdbuf->`[`pubsync`](../standard-library/basic-streambuf-class.md#pubsync)。 如果該調用返回 -1,則函[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`數 調用並返回 -1。 否則，此函式會傳回零。

## <a name="basic_istreamtellg"></a><a name="tellg"></a>basic_istream:泰爾格

回報在資料流中目前的讀取位置。

```cpp
pos_type tellg();
```

### <a name="return-value"></a>傳回值

在資料流中的目前位置。

### <a name="remarks"></a>備註

如果[`fail`](../standard-library/basic-ios-class.md#fail)為 false,則成員函[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)`->`[`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff)`(0, cur, in)`數 會傳回 。 否則會傳回 `pos_type(-1)`。

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

## <a name="basic_istreamunget"></a><a name="unget"></a>basic_istream::不獲取

將最近讀取的字元放回資料流。

```cpp
basic_istream<Char_T, Tr>& unget();
```

### <a name="return-value"></a>傳回值

串 __#这个__(#这个 ).

### <a name="remarks"></a>備註

如果可能,[未格式化的輸入函數](../standard-library/basic-istream-class.md)將流中的上一個元素放回原元素,就像`rdbuf->`[`sungetc`](../standard-library/basic-streambuf-class.md#sungetc)調用 一樣。 如果[`rdbuf`](../standard-library/basic-ios-class.md#rdbuf)為空指標,或者`sungetc`對的呼叫,`traits_type::`[`eof`](../standard-library/basic-ios-class.md#eof)則函數將[`setstate`](../standard-library/basic-ios-class.md#setstate)`(badbit)`呼叫 。 在任何情況下,它傳回 ___this__。

有關如何`unget`失敗的資訊,請[`basic_streambuf::sungetc`](../standard-library/basic-streambuf-class.md#sungetc)參閱 。

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

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
