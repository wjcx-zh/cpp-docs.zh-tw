---
title: basic_stringbuf 類別
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 578d0e31e08f3e077a908c4344f77da5495df40d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364880"
---
# <a name="basic_stringbuf-class"></a>basic_stringbuf 類別

描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與陣列物件中儲存的項目序列之間的往來傳輸。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>參數

*Alloc*\
配置器類別。

*埃萊姆*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

會視需要配置、擴充和釋出物件，以容納序列中的變更。

basic_stringbuf< `Elem`, `Tr`, `Alloc`> 類別的物件會將其建構函式中的 `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) 引數複本儲存為其 `stringbuf` 模式 **mode**：

- 如果 `mode & ios_base::in` 非零，輸入緩衝區即可存取。 如需詳細資訊，請參閱 [basic_streambuf 類別](../standard-library/basic-streambuf-class.md)。

- 如果 `mode & ios_base::out` 非零，輸出緩衝區即可存取。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|建構類型 `basic_stringbuf` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|該類型是範本參數*Alloc*的同義詞。|
|[char_type](#char_type)|將類型名稱與 *Elem* 範本參數建立關聯。|
|[int_type](#int_type)|使此類型在`basic_filebuf`的範圍中等效於*Tr*作用域中的相同名稱的類型。|
|[off_type](#off_type)|使此類型在`basic_filebuf`的範圍中等效於*Tr*作用域中的相同名稱的類型。|
|[pos_type](#pos_type)|使此類型在`basic_filebuf`的範圍中等效於*Tr*作用域中的相同名稱的類型。|
|[traits_type](#traits_type)|將類型名稱與 *Tr* 範本參數建立關聯。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[溢出](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|受保護的虛擬成員函式會嘗試將項目放回輸入緩衝區，然後將其設成目前的項目 (由下一個指標指向)。|
|[seekoff](#seekoff)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[seekpos](#seekpos)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[Str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|
|swap||
|[underflow](#underflow)|用於從輸入資料流擷取目前項目之受保護的虛擬成員函式。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="basic_stringbufallocator_type"></a><a name="allocator_type"></a>basic_stringbuf:allocator_type

該類型是範本參數*Alloc*的同義詞。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbufbasic_stringbuf"></a><a name="basic_stringbuf"></a>basic_stringbuf:basic_stringbuf

建構類型 `basic_stringbuf` 的物件。

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*Str*\
[basic_string](../standard-library/basic-string-class.md) 類型的物件。

### <a name="remarks"></a>備註

第一個建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存 Null 指標。 如需詳細資訊，請參閱 [basic_streambuf 類別](../standard-library/basic-streambuf-class.md)的＜備註＞一節。 它還存儲 *_Mode*為stringbuf模式。 如需詳細資訊，請參閱 [basic_stringbuf 類別](../standard-library/basic-stringbuf-class.md)的＜備註＞一節。

第二個建構函數分配由字串物件*str*控制的序列的副本。 如果 `_Mode & ios_base::in` 為非零值，它會設定輸入緩衝區從序列開頭開始讀取。 如果 `_Mode & ios_base::out` 為非零值，它會設定輸出緩衝區從序列開頭開始寫入。 它還存儲 *_Mode*為stringbuf模式。 如需詳細資訊，請參閱 [basic_stringbuf 類別](../standard-library/basic-stringbuf-class.md)的＜備註＞一節。

## <a name="basic_stringbufchar_type"></a><a name="char_type"></a>basic_stringbuf:char_type

將類型名稱與 *Elem* 範本參數建立關聯。

```cpp
typedef Elem char_type;
```

## <a name="basic_stringbufint_type"></a><a name="int_type"></a>basic_stringbuf:int_type

使此類型basic_filebuf範圍中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_stringbufoff_type"></a><a name="off_type"></a>basic_stringbuf:off_type

使此類型basic_filebuf範圍中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_stringbufoverflow"></a><a name="overflow"></a>basic_stringbuf:溢出

受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*\
要插入緩衝區的字元，或 `traits_type::eof`。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `traits_type::eof`。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>備註

如果*\_Meta*不比較等於**traits_type:**[eof](../standard-library/char-traits-struct.md#eof),則受保護的虛擬成員函數將嘗試將元素**traits_type:to_char_type**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)*\_(Meta)* 插入到輸出緩衝區中。 它可以透過下列各種方式來執行：

- 如果有寫入位置可供使用，它可以將項目儲存至寫入位置，並遞增輸出緩衝區的下一個指標。

- 為輸出緩衝區配置新的或額外的儲存空間，即可提供寫入位置。 以這種方式擴充輸出緩衝區時，也會擴充任何相關的輸入緩衝區。

## <a name="basic_stringbufpbackfail"></a><a name="pbackfail"></a>basic_stringbuf::p回擊失敗

受保護的虛擬成員函式會嘗試將元素放回輸入緩衝區，然後將其設成目前的元素 (由下一個指標指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

*_Meta*\
要插入緩衝區的字元，或 `traits_type::eof`。

### <a name="return-value"></a>傳回值

如果函式不成功，則會傳回 `traits_type::eof`。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>備註

如果 *_Meta*與**traits_type:eof**[eof](../standard-library/char-traits-struct.md#eof)進行比較,則要回滾的元素實際上是當前元素之前流中已有的元素。 否則,該元素將被**位元** = **traits_type:to_char_type**[(*](../standard-library/char-traits-struct.md#to_char_type) *Meta*) 替換。 函式可透過下列各種方式來放回項目：

- 如果有 putback 位置可供使用，而且儲存在其中的元素與位元組比較的結果相等，則可以遞減輸入緩衝區的下一個指標。

- 如果有 putback 位置可供使用，而且 stringbuf 模式允許改變序列 (**mode & ios_base::out** 為非零值)，則可以將位元組儲存在 putback 位置，並遞減輸入緩衝區的下一個指標。

## <a name="basic_stringbufpos_type"></a><a name="pos_type"></a>basic_stringbuf::pos_類型

使此類型basic_filebuf範圍中等效於`Tr`作用域中的相同名稱的類型。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_stringbufseekoff"></a><a name="seekoff"></a>basic_stringbuf::尋求

受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Off*\
相對於 *_Way*尋求的位置。 如需詳細資訊，請參閱 [basic_stringbuf::off_type](#off_type)。

*_Way*\
位移作業的起點。 如需可能的值，請參閱 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)。

*_Mode*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置。

### <a name="remarks"></a>備註

針對 `basic_stringbuf<Elem, Tr, Alloc>` 類別的物件，資料流位置完全是由資料流位移所組成。 位移零會指定受控制序列的第一個項目。

新位置的判斷如下：

- 如果 ,新位置是流的開始加上 _Off 。*_Off* `_Way`  == `ios_base::beg`

- 如果 ,新位置是當前流位置加上 _Off 。*_Off* `_Way`  == `ios_base::cur`

- 如果 ,新位置是流的末尾加上 _Off 。*_Off* `_Way`  == `ios_base::end`

如果 `_Mode & ios_base::in` 為非零值，此函式會改變要讀入輸入緩衝區的下一個位置。 如果 `_Mode & ios_base::out` 為非零值，此函式會改變要寫入輸出緩衝區的下一個位置。 若要影響資料流，其緩衝區必須存在。 若要讓置放作業能夠成功，產生的資料流位置必須位於受控制的序列內。 如果函數影響兩個流位置,*則必須*_Way`ios_base::beg`或`ios_base::end`,並且兩個流都位於同一元素中。 否則 (若不影響任一位置)，置放作業會失敗。

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。

## <a name="basic_stringbufseekpos"></a><a name="seekpos"></a>basic_stringbuf::尋求者

受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Sp*\
要搜尋的位置。

*_Mode*\
指定指標位置的模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

針對 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件，資料流位置完全是由資料流位移所組成。 位移零會指定受控制序列的第一個項目。 新位置是由 _ *Sp* 所來判斷。

如果 **mode & ios_base::in** 為非零值，此函式會改變要讀入輸入緩衝區的下一個位置。 如果 **mode & ios_base::out** 為非零值，此函式會改變要寫入輸出緩衝區的下一個位置。 若要影響資料流，其緩衝區必須存在。 若要讓置放作業能夠成功，產生的資料流位置必須位於受控制的序列內。 否則 (若不影響任一位置)，置放作業會失敗。

## <a name="basic_stringbufstr"></a><a name="str"></a>basic_stringbuf:斯特

設定或取得字串緩衝區中的文字，而不需要變更寫入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>參數

*_Newstr*\
新字串。

### <a name="return-value"></a>傳回值

傳回 [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回 basic_string< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。 複製的序列取決於預存的 stringbuf 模式：

- 如果 **mode &amp; ios_base::out** 為非零值，而且存在輸出緩衝區，此序列是整個輸出緩衝區 ([epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) 元素，從 `pbase` 開始)。

- 如果 **mode &amp; ios_base::in** 為非零值，而且存在輸入緩衝區，此序列是整個輸入緩衝區 ([egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) 元素，從 `eback` 開始)。

- 否則，複製的序列是空的。

第二個成員函數將解分配當前由**\*它**控制的任何序列。 然後,它分配由 *_Newstr*控制序列的副本。 如果 **mode & ios_base::in** 為非零值，它會設定輸入緩衝區從序列開頭開始讀取。 如果 **mode & ios_base::out** 為非零值，它會設定輸出緩衝區從序列開頭開始寫入。

### <a name="example"></a>範例

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="basic_stringbuftraits_type"></a><a name="traits_type"></a>basic_stringbuf:traits_type

將類型名稱與 *Tr* 範本參數建立關聯。

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數 *Tr* 同義。

## <a name="basic_stringbufunderflow"></a><a name="underflow"></a>basic _ stringbuf :

用於從輸入資料流擷取目前項目之受保護的虛擬函式。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>傳回值

如果函數無法成功,它將返回**traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。 否則會傳回輸入資料流中已轉換的目前元素。

### <a name="remarks"></a>備註

受保護的虛擬成員函數嘗試從輸入緩衝區中提取當前元素`byte`,推進當前流位置,並將該元素返回為**traits_type:to_int_type**[(](../standard-library/char-traits-struct.md#to_int_type)**位元組**)。 它可以以一種方式做到這一點:如果讀取位置可用,它將作為`byte`存儲在讀取位置的元素,並推進輸入緩衝區的下一個指標。

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::交換

將此字串緩衝區的內容與另一個字串緩衝區交換。

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>參數

*其他*\
內容即將與此 basic_stringbuf 交換的 basic_stringbuf。

### <a name="remarks"></a>備註

## <a name="basic_stringbufoperator"></a><a name="op_eq"></a>basic_stringbuf::操作員*

將運算子右邊的 basic_stringbuf 內容指派到左邊的 basic_stringbuf。

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>參數

*其他*\
其內容 (包括地區設定特性) 將被指派到運算子左邊 stringbuf 的 basic_stringbuf。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
