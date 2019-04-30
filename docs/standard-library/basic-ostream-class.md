---
title: basic_ostream 類別
ms.date: 03/27/2019
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
ms.openlocfilehash: 64a32513e9dc151e64fccdb0ef678a75588f0a41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371646"
---
# <a name="basicostream-class"></a>basic_ostream 類別

此範本類別描述的物件可控制插入的項目和編碼的物件類型的項目使用的資料流緩衝區`Elem`也稱為[char_type](../standard-library/basic-ios-class.md#char_type)，其字元特性由類別`Tr`也稱為[traits_type](../standard-library/basic-ios-class.md#traits_type)。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>參數

*Elem*<br/>
`char_type`。

*Tr*<br/>
字元 `traits_type`。

## <a name="remarks"></a>備註

大部分多載 [operator<<](#basic_ostream_operator_lt_lt) 的成員函式為格式化的輸出函式。 它們遵循下列模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{try
{<convert and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

其他兩個成員函式是未格式化的輸出函式。 它們遵循下列模式：

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
{try
{<obtain and insert elements
    accumulate flags in state> }
    catch (...)
{try
{setstate(badbit);

}
    catch (...)
{}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

這兩個群組的函式呼叫[setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) 如果在插入項目時遭遇失敗。

basic_istream\< **Elem**, **Tr**> 類別的物件只會儲存 [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>** 類別的虛擬公用基底物件。

## <a name="example"></a>範例

若要深入了解輸出資料流，請參閱 [basic_ofstream 類別](../standard-library/basic-ofstream-class.md)的範例。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_ostream](#basic_ostream)|建構 `basic_ostream` 物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[flush](#flush)|清除緩衝區。|
|[put](#put)|將字元置入資料流中。|
|[seekp](#seekp)|重設輸出資料流中的位置。|
|[sentry](#sentry)|此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。|
|[swap](#swap)|用所提供的 `basic_ostream` 物件的值交換這個 `basic_ostream` 物件中的值。|
|[tellp](#tellp)|報告輸出資料流中的位置。|
|[write](#write)|將字元置入資料流中。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|將提供的 `basic_ostream` 物件參數值指派為這個物件。|
|[operator<<](#basic_ostream_operator_lt_lt)|寫入資料流。|

## <a name="requirements"></a>需求

**標頭︰**\<ostream>

**命名空間：** std

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

建構 `basic_ostream` 物件。

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>參數

*strbuf*<br/>
[basic_streambuf](../standard-library/basic-streambuf-class.md) 類型的物件。

*_Isstd*<br/>
**true**如果這是標準的資料流; 否則**false**。

*right*<br/>
類型為 `basic_ostream` 之物件的右值參考。

### <a name="remarks"></a>備註

第一個建構函式會藉由呼叫 [init](../standard-library/basic-ios-class.md#init)(`strbuf`) 初始化基底類別。 第二個建構函式會藉由呼叫 [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)` 初始化基底類別。

### <a name="example"></a>範例

若要深入了解輸出資料流，請參閱 [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 的範例。

## <a name="flush"></a>  basic_ostream::flush

清除緩衝區。

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

如果 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) 不是 null 指標，函式會呼叫 **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync)。 如果傳回 -1，函式會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**)。 它會傳回 **\*this**。

### <a name="example"></a>範例

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostream_operator_lt_lt"></a>  basic_ostream::operator&lt;&lt;

寫入資料流。

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>參數

*Pfn*<br/>
函式指標。

*strbuf*<br/>
`stream_buf` 物件的指標。

*val*<br/>
要寫入至資料流的元素。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

\<Ostream > 標頭也會定義數個全域插入運算子。 如需詳細資訊，請參閱 <<c0> [ 運算子 <<](../standard-library/ostream-operators.md#op_lt_lt)。

第一個成員函式可確保表單的運算式`ostr << endl`呼叫[endl](../standard-library/ostream-functions.md#endl)**(ostr)**，然後傳回**\*這**。 第二個和第三個函式可確保其他操作工具 (例如 [hex](../standard-library/ios-functions.md#hex)) 具有類似的行為。 其餘函式都是格式化的輸出函式。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

擷取中的項目*strbuf*，如果*strbuf*不是 null 指標，並將其插入。 擷取會在檔案結尾處停止，或在擷取擲回例外狀況時停止 (此例外狀況會再次擲回)。 如果插入失敗，它也會停止，而不會擷取有問題的元素。 如果函式未插入任何元素，或是擷取擲回例外狀況，函式會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 在任何情況下，此函式都會傳回 **\*this**。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

將轉換`_Val`為布林值欄位，並將它插入藉由呼叫[use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put\<Elem，Outit> >**`(`[getloc](../standard-library/ios-base-class.md#getloc))。 [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**)。 在這裡，`OutIt`指[ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem，Tr> >**。 此函式會傳回 **\*this**。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

每個轉換*val*為數值欄位，並將其插入呼叫**use_facet < num_put\<Elem，Outit> >**(`getloc`)。 **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**)。 此處的 **OutIt** 會定義為 **ostreambuf_iterator\<Elem, Tr>**。 此函式會傳回 **\*this**。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

每個轉換*val*為數值欄位，並將其插入呼叫**use_facet < num_put\<Elem，Outit> >**(`getloc`)**。 放**(**OutIt**(`rdbuf`)， **\*這**， `getloc`， **val**)。 此處的 **OutIt** 會定義為 **ostreambuf_iterator\<Elem, Tr>**。 此函式會傳回 **\*this**。

### <a name="example"></a>範例

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="op_eq"></a>  basic_ostream::operator=

將提供的 `basic_ostream` 物件參數值指派給這個物件。

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>參數

*right*<br/>
`basic_ostream` 物件的 `rvalue` 參考。

### <a name="remarks"></a>備註

這個成員運算子會呼叫 swap `(right)`。

## <a name="put"></a>  basic_ostream::put

將字元置入資料流中。

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*<br/>
字元。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

未格式化的輸出函式會插入之項目的 *_Ch*。 它會傳回 **\*this**。

### <a name="example"></a>範例

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="seekp"></a>  basic_ostream::seekp

重設輸出資料流中的位置。

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>參數

*_Pos*<br/>
資料流中的位置。

*_Off*<br/>
相對位移 *_Way*。

*_Way*<br/>
其中一個 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 列舉。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

如果[失敗](../standard-library/basic-ios-class.md#fail)是**false**，第一個成員函式呼叫**newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->**[pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*)，某些`pos_type`暫存物件`newpos`。 如果`fail`為 false，第二個函式會呼叫**newpos = rdbuf-> >** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off，_Way*)。 在任一情況下，如果 (`off_type`)**newpos ==** (`off_type`)(-1) (置放作業失敗)，則函式會呼叫 **istr.**[setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 兩個函式都會傳回 **\*this**。

### <a name="example"></a>範例

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="sentry"></a>  basic_ostream::sentry

此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。

類別 sentry {public： 明確 sentry (basic_ostream\<Elem，Tr> > & _Ostr); 運算子 bool （) const; ~ sentry();};

### <a name="remarks"></a>備註

此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。 如果 **ostr.**[good](../standard-library/basic-ios-class.md#good) 為 **true** 且 **ostr.**[tie](../standard-library/basic-ios-class.md#tie) 不是 null 指標，建構函式會呼叫 **ostr.tie->**[flush](#flush)。 建構函式將儲存所傳回的值`ostr.good`在`status`。 稍後呼叫`operator bool`提供此預存的值。

如果 `uncaught_exception` 傳回 **false** 且 [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) 為非零值，解構函氏會呼叫 [flush](#flush)。

## <a name="swap"></a>  basic_ostream::swap

用所提供的 `basic_ostream` 的值交換這個 `basic_ostream` 物件的值。

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>參數

*right*<br/>
對 `basic_ostream` 物件的參考。

### <a name="remarks"></a>備註

成員函式呼叫[basic_ios:: swap](../standard-library/basic-ios-class.md#swap) `(right)`的內容，此物件的內容交換*右*。

## <a name="tellp"></a>  basic_ostream::tellp

報告輸出資料流中的位置。

```cpp
pos_type tellp();
```

### <a name="return-value"></a>傳回值

輸出資料流中的位置。

### <a name="remarks"></a>備註

如果 [fail](../standard-library/basic-ios-class.md#fail) 為 **false**，成員函式會傳回 [rdbuf](../standard-library/basic-ios-class.md#rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**)。 否則會傳回 `pos_type`(-1)。

### <a name="example"></a>範例

如需 `tellp` 的使用範例，請參閱 [seekp](#seekp)。

## <a name="write"></a>  basic_ostream::write

將字元置入資料流中。

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>參數

*count*<br/>
要置入資料流中的字元計數。

*str*<br/>
要置入資料流中的字元。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

[未格式化的輸出函式](../standard-library/basic-ostream-class.md)插入序列*計數*開頭的項目*str*。

### <a name="example"></a>範例

如需 `write` 的使用範例，請參閱 [streamsize](../standard-library/ios-typedefs.md#streamsize)。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
