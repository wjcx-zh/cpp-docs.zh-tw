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
ms.openlocfilehash: e074eb30d31c316411dd43f9a7a019defb64e9fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376770"
---
# <a name="basic_ostream-class"></a>basic_ostream 類別

類範本`Elem`描述一個物件,該物件控制將元素和編碼的物件插入具有類型元素(也稱為[char_type)](../standard-library/basic-ios-class.md#char_type)的流緩衝區中,其字元`Tr`特徵由類 (也稱為[traits_type)](../standard-library/basic-ios-class.md#traits_type)確定。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>參數

*埃萊姆*\
`char_type`。

*Tr*\
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

如果兩組函數在插入元素時遇到故障,則調用[setstate](../standard-library/basic-ios-class.md#setstate)(**badbit)。**

basic_istream\< **Elem**, **Tr**> 類別的物件只會儲存 [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>** 類別的虛擬公用基底物件。

## <a name="example"></a>範例

若要深入了解輸出資料流，請參閱 [basic_ofstream 類別](../standard-library/basic-ofstream-class.md)的範例。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_ostream](#basic_ostream)|建構 `basic_ostream` 物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[沖洗](#flush)|清除緩衝區。|
|[把](#put)|將字元置入資料流中。|
|[seekp](#seekp)|重設輸出資料流中的位置。|
|[sentry](#sentry)|此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。|
|[交換](#swap)|用所提供的 `basic_ostream` 物件的值交換這個 `basic_ostream` 物件中的值。|
|[tellp](#tellp)|報告輸出資料流中的位置。|
|[寫](#write)|將字元置入資料流中。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|將提供的 `basic_ostream` 物件參數值指派為這個物件。|
|[運算子<<](#basic_ostream_operator_lt_lt)|寫入資料流。|

## <a name="requirements"></a>需求

**標頭︰** \<ostream>

**命名空間：** std

## <a name="basic_ostreambasic_ostream"></a><a name="basic_ostream"></a>basic_ostream:basic_ostream

建構 `basic_ostream` 物件。

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>參數

*斯特布夫*\
[basic_streambuf](../standard-library/basic-streambuf-class.md) 類型的物件。

*_Isstd*\
如果這是標準流,**則為 true;** 否則,**假**。

*對*\
類型為 `basic_ostream` 之物件的右值參考。

### <a name="remarks"></a>備註

第一個建構函數通過調用[init](../standard-library/basic-ios-class.md#init)`strbuf`() 初始化基類。 第二個構造函數通過調用[basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`來初始化基類。

### <a name="example"></a>範例

若要深入了解輸出資料流，請參閱 [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 的範例。

## <a name="basic_ostreamflush"></a><a name="flush"></a>basic_ostream:沖洗

清除緩衝區。

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

如果 [rdbuf](../standard-library/basic-ios-class.md#rdbuf) 不是 null 指標，函式會呼叫 **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync)。 如果傳回 -1，函式會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**)。 傳回**\*此**。

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

## <a name="basic_ostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt"></a>basic_ostream::操作員&lt;&lt;

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

*普芬*\
函式指標。

*斯特布夫*\
`stream_buf` 物件的指標。

*瓦爾*\
要寫入至資料流的元素。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

\<ostream>标头还定义了多个全局插入运算符。 有關詳細資訊,請參閱[運算符<<](../standard-library/ostream-operators.md#op_lt_lt)。

第一個成員函數`ostr << endl`確保表單的表示式呼叫[endl](../standard-library/ostream-functions.md#endl)**(ostr),** 然後傳回**\*此**。 第二個和第三個函式可確保其他操作工具 (例如 [hex](../standard-library/ios-functions.md#hex)) 具有類似的行為。 其餘函式都是格式化的輸出函式。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

如果*strbuf*不是空指標,則從*strbuf*中提取元素,並插入它們。 擷取會在檔案結尾處停止，或在擷取擲回例外狀況時停止 (此例外狀況會再次擲回)。 如果插入失敗，它也會停止，而不會擷取有問題的元素。 如果函式未插入任何元素，或是擷取擲回例外狀況，函式會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**)。 在任何情況下,函數會傳回**\*此**。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

`_Val`轉換為布林欄位,並透過調用num_put** \<Elem、Outit>** `(` [getloc](../standard-library/ios-base-class.md#getloc) [<use_facet](../standard-library/basic-filebuf-class.md#open)插入它。 [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**)。 這裡,`OutIt`定義為[ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<埃萊姆,Tr>**。 函數傳回**\*此**。

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

每個將*val*轉換為數位欄位,並透過呼叫**use_facet<num_put\<Elem、OutIt ** `getloc`>() use_facet插入它。 **放****(OutIt**`rdbuf`( `getloc`),**\*這個**, ,**瓦爾**). 此處的 **OutIt** 會定義為 **ostreambuf_iterator\<Elem, Tr>**。 函數傳回**\*此**。

函式

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

每個轉換*val*到一個數位欄位,並透過呼叫**use_facet<num_put\<Elem,OutIt>**()`getloc``rdbuf`**.put**( `getloc` **OutIt**( ),**\*這個**, **val**) 插入它。 此處的 **OutIt** 會定義為 **ostreambuf_iterator\<Elem, Tr>**。 函數傳回**\*此**。

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

## <a name="basic_ostreamoperator"></a><a name="op_eq"></a>basic_ostream::操作員*

將提供的 `basic_ostream` 物件參數值指派給這個物件。

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_ostream` 物件的 `rvalue` 參考。

### <a name="remarks"></a>備註

這個成員運算子會呼叫 swap `(right)`。

## <a name="basic_ostreamput"></a><a name="put"></a>basic_ostream::p烏特

將字元置入資料流中。

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>參數

*_Ch*\
字元。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

未格式化的輸出函數將元素 *_Ch*插入。 傳回**\*此**。

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

## <a name="basic_ostreamseekp"></a><a name="seekp"></a>basic_ostream:seekp

重設輸出資料流中的位置。

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>參數

*_Pos*\
資料流中的位置。

*_Off*\
相對於 *_Way*的偏移量。

*_Way*\
其中一個 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) 列舉。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

如果[失敗](../standard-library/basic-ios-class.md#fail)**為 false,** 則第一個成員函數呼叫**newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos(_Pos),](../standard-library/basic-streambuf-class.md#pubseekpos)用於 *_Pos*某些`pos_type`臨時物件。 `newpos` 如果`fail`為 false,則第二個函數調用**newpos = rdbuf->** [pubseekoff(_Off,_Way](../standard-library/basic-streambuf-class.md#pubseekoff))。* * 在這兩種情況下,`off_type`如果 ( )**newpos =** (`off_type`-1) (定位操作失敗), 則函數調用**istr。**[設定狀態](../standard-library/basic-ios-class.md#setstate)(**失敗位**)。 兩個函數都傳回**\*此**。

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

## <a name="basic_ostreamsentry"></a><a name="sentry"></a>basic_ostream:哨兵

此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。

類哨兵 = 公共:顯式哨兵\<(basic_ostream Elem,Tr>& _Ostr);操作者 bool() const;[哨兵();*;

### <a name="remarks"></a>備註

此巢狀的類別會描述物件，該物件的宣告會將格式化輸出函式和未格式化輸出函式結構化。 如果 **ostr.**[good](../standard-library/basic-ios-class.md#good) 為 **true** 且 **ostr.**[tie](../standard-library/basic-ios-class.md#tie) 不是 null 指標，建構函式會呼叫 **ostr.tie->**[flush](#flush)。 然後,構造函數將返回`ostr.good`的值存儲在`status`中。 稍後調用以`operator bool`傳遞此存儲值。

如果 `uncaught_exception` 傳回 **false** 且 [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) 為非零值，解構函氏會呼叫 [flush](#flush)。

## <a name="basic_ostreamswap"></a><a name="swap"></a>basic_ostream:交換

用所提供的 `basic_ostream` 的值交換這個 `basic_ostream` 物件的值。

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_ostream` 物件的參考。

### <a name="remarks"></a>備註

成員函數調用[basic_ios::交換](../standard-library/basic-ios-class.md#swap)`(right)`來交換此對象的內容,以交換*權利*的內容。

## <a name="basic_ostreamtellp"></a><a name="tellp"></a>basic_ostream:tellp

報告輸出資料流中的位置。

```cpp
pos_type tellp();
```

### <a name="return-value"></a>傳回值

輸出資料流中的位置。

### <a name="remarks"></a>備註

如果[失敗](../standard-library/basic-ios-class.md#fail)**為 false,** 則成員函數傳回[rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`,**在**中 。 否則會傳回 `pos_type`(-1)。

### <a name="example"></a>範例

如需 `tellp` 的使用範例，請參閱 [seekp](#seekp)。

## <a name="basic_ostreamwrite"></a><a name="write"></a>basic_ostream::寫入

將字元置入資料流中。

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>參數

*計數*\
要置入資料流中的字元計數。

*Str*\
要置入資料流中的字元。

### <a name="return-value"></a>傳回值

basic_ostream 物件的參考。

### <a name="remarks"></a>備註

[未格式化輸出函數](../standard-library/basic-ostream-class.md)插入從*str*開始的*計數*元素序列。

### <a name="example"></a>範例

如需 `write` 的使用範例，請參閱 [streamsize](../standard-library/ios-typedefs.md#streamsize)。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
