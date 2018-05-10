---
title: basic_stringbuf 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7ec812ffeb50e83d59df764224ed9dcdaf07d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="basicstringbuf-class"></a>basic_stringbuf 類別

描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與陣列物件中儲存的項目序列之間的往來傳輸。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>參數

`Alloc` 配置器類別。

`Elem` 字串的基本項目的類型。

`Tr` 字元特性是字串的基本項目上特製化。

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
|[allocator_type](#allocator_type)|此類型是範本參數 `Alloc`的同義字。|
|[char_type](#char_type)|將類型名稱與 `Elem` 樣板參數產生關聯。|
|[int_type](#int_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[off_type](#off_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[pos_type](#pos_type)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|
|[traits_type](#traits_type)|將類型名稱與 `Tr` 樣板參數產生關聯。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[overflow](#overflow)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|
|[pbackfail](#pbackfail)|受保護的虛擬成員函式會嘗試將項目放回輸入緩衝區，然後將其設成目前的項目 (由下一個指標指向)。|
|[seekoff](#seekoff)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[seekpos](#seekpos)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|
|swap||
|[underflow](#underflow)|用於從輸入資料流擷取目前項目之受保護的虛擬成員函式。|

## <a name="requirements"></a>需求

**標頭︰**\<sstream>

**命名空間：** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

此類型是範本參數 `Alloc`的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

建構類型 `basic_stringbuf` 的物件。

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

`_Mode` 其中一個列舉中[ios_base:: openmode](../standard-library/ios-base-class.md#openmode)。

`str` 型別的物件[basic_string](../standard-library/basic-string-class.md)。

### <a name="remarks"></a>備註

第一個建構函式會在控制輸入緩衝區和輸出緩衝區的所有指標中儲存一個 null 指標。 如需詳細資訊，請參閱 [basic_streambuf 類別](../standard-library/basic-streambuf-class.md)的＜備註＞一節。 它也會將 `_Mode` 儲存為 stringbuf 模式。 如需詳細資訊，請參閱 [basic_stringbuf 類別](../standard-library/basic-stringbuf-class.md)的＜備註＞一節。

第二個建構函式會配置字串物件 `str` 所控制的序列複本。 如果 `_Mode & ios_base::in` 為非零值，它會設定輸入緩衝區從序列開頭開始讀取。 如果 `_Mode & ios_base::out` 為非零值，它會設定輸出緩衝區從序列開頭開始寫入。 它也會將 `_Mode` 儲存為 stringbuf 模式。 如需詳細資訊，請參閱 [basic_stringbuf 類別](../standard-library/basic-stringbuf-class.md)的＜備註＞一節。

## <a name="char_type"></a>  basic_stringbuf::char_type

將類型名稱與 **Elem** 樣板參數產生關聯。

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::overflow

受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

`_Meta` 要插入到緩衝區的字元或**traits_type::eof**。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof**。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>備註

如果 _ *Meta* 與 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof) 比較的結果不相等，此受保護的虛擬成員函式會嘗試將元素 **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) 插入輸出緩衝區。 它可以透過下列各種方式來執行：

- 如果有寫入位置可供使用，它可以將元素儲存在寫入位置，並遞增輸出緩衝區的下一個指標。

- 藉由為輸出緩衝區配置新的或額外的儲存體，即可提供寫入位置。 以這種方式擴充輸出緩衝區時，也會擴充任何相關輸入緩衝區。

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

此受保護的虛擬成員函式會嘗試將元素放回輸入緩衝區，然後將其設成目前的元素 (由下一個指標指向)。

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>參數

`_Meta` 要插入到緩衝區的字元或**traits_type::eof**。

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::eof**。 否則會傳回 **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*)。

### <a name="remarks"></a>備註

如果 `_Meta` 與 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof) 比較的結果相等，要推回的元素實際上是一個已在資料流中目前元素之前的元素。 否則會以 **byte** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*) 取代該元素。 此函式可以透過下列各種方式來放回元素：

- 如果有 putback 位置可供使用，而且儲存在其中的元素與位元組比較的結果相等，則可以遞減輸入緩衝區的下一個指標。

- 如果有 putback 位置可供使用，而且 stringbuf 模式允許改變序列 (**mode & ios_base::out** 為非零值)，則可以將位元組儲存在 putback 位置，並遞減輸入緩衝區的下一個指標。

## <a name="pos_type"></a>  basic_stringbuf::pos_type

使 basic_filebuf 範圍中的這個類型，相當於 **Tr** 範圍中的同名類型。

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

`_Off` 要搜尋的相對位置`_Way`。 如需詳細資訊，請參閱 [basic_stringbuf::off_type](#off_type)。

`_Way` 位移作業的起點。 如需可能的值，請參閱 [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir)。

`_Mode` 指定指標的位置模式。 預設為允許您修改讀取和寫入位置。 如需詳細資訊，請參閱 [ios_base::openmode](../standard-library/ios-base-class.md#openmode)。

### <a name="return-value"></a>傳回值

傳回新位置或無效的資料流位置。

### <a name="remarks"></a>備註

針對 `basic_stringbuf<Elem, Tr, Alloc>` 類別的物件，資料流位置完全是由資料流位移所組成。 位移零指定受控制序列的第一個元素。

新位置的判斷如下：

- 如果 `_Way` == `ios_base::beg`，新位置是資料流開頭加上 `_Off`。

- 如果 `_Way` == `ios_base::cur`，新位置是目前的資料流位置加上 `_Off`。

- 如果 `_Way` == `ios_base::end`，新位置是資料流結尾加上 `_Off`。

如果 `_Mode & ios_base::in` 為非零值，此函式會改變要讀入輸入緩衝區的下一個位置。 如果 `_Mode & ios_base::out` 為非零值，此函式會改變要寫入輸出緩衝區的下一個位置。 若要影響資料流，其緩衝區必須存在。 若要讓置放作業能夠成功，產生的資料流位置必須位於受控制的序列內。 如果函式會影響這兩個資料流位置，`_Way` 必須是 `ios_base::beg` 或 `ios_base::end`，並將這兩個資料流置放於相同的元素。 否則 (若不影響任一位置)，置放作業會失敗。

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。

## <a name="seekpos"></a>  basic_stringbuf::seekpos

受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

`_Sp` 要搜尋的位置。

`_Mode` 指定指標的位置模式。 預設為允許您修改讀取和寫入位置。

### <a name="return-value"></a>傳回值

如果函式成功改變一個或兩個資料流位置，則會傳回結果資料流位置。 否則會失敗，並傳回無效的資料流位置。 若要判斷資料流位置是否無效，請比較傳回值與 `pos_type(off_type(-1))`。

### <a name="remarks"></a>備註

針對 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件，資料流位置完全是由資料流位移所組成。 位移零會指定受控制序列的第一個項目。 新位置是由 _ *Sp* 所決定。

如果 **mode & ios_base::in** 為非零值，此函式會改變要讀入輸入緩衝區的下一個位置。 如果 **mode & ios_base::out** 為非零值，此函式會改變要寫入輸出緩衝區的下一個位置。 若要影響資料流，其緩衝區必須存在。 若要讓置放作業成功，產生的資料流位置必須位於受控制的序列內。 否則 (若不影響任一位置)，置放作業會失敗。

## <a name="str"></a>  basic_stringbuf::str

設定或取得字串緩衝區中的文字，而不需要變更寫入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>參數

`_Newstr` 新的字串。

### <a name="return-value"></a>傳回值

傳回 [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回 basic_string< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。 複製的序列取決於預存的 stringbuf 模式：

- 如果 **mode &amp; ios_base::out** 為非零值，而且存在輸出緩衝區，此序列是整個輸出緩衝區 ([epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) 元素，從 `pbase` 開始)。

- 如果 **mode &amp; ios_base::in** 為非零值，而且存在輸入緩衝區，此序列是整個輸入緩衝區 ([egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) 元素，從 `eback` 開始)。

- 否則，複製的序列是空的。

第二個成員函式會解除配置 **\*this** 目前所控制的任何序列。 然後會配置 `_Newstr` 所控制的序列複本。 如果 **mode & ios_base::in** 為非零值，它會設定輸入緩衝區從序列開頭開始讀取。 如果 **mode & ios_base::out** 為非零值，它會設定輸出緩衝區從序列開頭開始寫入。

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

## <a name="traits_type"></a>  basic_stringbuf::traits_type

將類型名稱與 **Tr** 範本參數建立關聯。

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數 **Tr** 同義。

## <a name="underflow"></a>  basic_stringbuf::underflow

用於從輸入資料流擷取目前項目之受保護的虛擬函式。

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>傳回值

如果函式不成功，則傳回 **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)。 否則會傳回輸入資料流中已轉換的目前元素。

### <a name="remarks"></a>備註

此受保護的虛擬成員函式會嘗試從輸入緩衝區擷取目前的元素 **byte**，從目前的資料流位置前移，並傳回此元素作為 **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **byte**)。 它可以透過下列其中一種方式來執行︰如果有讀取位置可供使用，它會採用 **byte** 作為儲存在讀取位置中的元素，並前進到輸入緩衝區的下一個指標。

## <a name="swap"></a>  basic_streambuf::swap

將此字串緩衝區的內容與另一個字串緩衝區交換。

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>參數

`other` Basic_stringbuf 將交換的內容與此 basic_stringbuf。

### <a name="remarks"></a>備註

## <a name="op_eq"></a>  basic_stringbuf::operator=

將運算子右邊的 basic_stringbuf 內容指派到左邊的 basic_stringbuf。

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>參數

`other` 其內容，包括地區設定特性，將被指派到運算子左邊 stringbuf 的 basic_stringbuf。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
