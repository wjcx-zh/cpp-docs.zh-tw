---
title: basic_ifstream 類別
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: f4f5ddd3d1c0c595dd1661fab73f5267fb161593
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219283"
---
# <a name="basic_ifstream-class"></a>basic_ifstream 類別

描述一個物件，它會從[basic_filebuf](../standard-library/basic-filebuf-class.md)類別的資料流程緩衝區> （具有類型的元素）控制專案和編碼物件的提取， <  `Elem` `Tr` `Elem` 其字元特性是由類別所決定 `Tr` 。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Elem*\
檔案緩衝區的基本項目。

*Tr*\
檔案緩衝區之基本元素的特性 (通常是 `char_traits`< `Elem`>)。

## <a name="remarks"></a>備註

此物件會儲存 `basic_filebuf`< `Elem`, `Tr`> 類別的物件。

## <a name="example"></a>範例

下列範例示範如何在檔案的文字中讀取。

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>輸入：basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>輸出

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_ifstream](#basic_ifstream)|初始化 `basic_ifstream` 物件的新執行個體。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[關閉](#close)|關閉檔案。|
|[is_open](#is_open)|判斷檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[rdbuf](#rdbuf)|傳回預存資料流緩衝區的位址。|
|[調換](#swap)|將此 `basic_ifstream` 的內容和提供的 `basic_ifstream` 內容交換。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator =](#op_eq)|指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的 `rvalue`。|

## <a name="requirements"></a>需求

**標頭：**\<fstream>

**命名空間：** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream：： basic_ifstream

建構類型 `basic_ifstream` 的物件。

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>參數

*_Filename*\
要開啟之檔案的名稱。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*_Prot*\
預設檔案開啟保護，相當於 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 參數。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫[basic_istream](../standard-library/basic-istream-class.md)（）來初始化基類 `sb` ，其中 `sb` 是類別[basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` ，> 的預存物件 `Tr` 。 它也會藉由呼叫 `basic_filebuf`< `Elem`, `Tr`> 初始化 `sb`。

第二個和第三個建構函式會藉由呼叫 `basic_istream`( `sb`) 初始化基底類別。 它也會藉 `sb` 由呼叫[basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf) <  `Elem` 、 `Tr`>，然後 `sb` 進行初始化。 [開啟](../standard-library/basic-filebuf-class.md#open)（ `_Filename` ， `_Mode` &#124; `ios_base::in` ）。 如果後面一個函式傳回 null 指標，則此函式會呼叫**setstate**（ `failbit` ）。

第四個建構函式會使用視為右值參考的 `right` 內容初始化物件。

### <a name="example"></a>範例

下列範例示範如何在檔案的文字中讀取。 若要建立檔案，請參閱 [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 的範例。

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream：： close

關閉檔案。

```cpp
void close();
```

### <a name="remarks"></a>備註

此成員函式會呼叫[rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>範例

如需使用 `close` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream：： is_open

判斷檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果檔案已開啟，則為， **`false`** 否則為。

### <a name="remarks"></a>備註

此成員函式會傳回[rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>範例

如需使用 `is_open` 的範例，請參閱 [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream：： open

開啟檔案。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>參數

*_Filename*\
要開啟之檔案的名稱。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*_Prot*\
預設檔案開啟保護，相當於 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 參數。

### <a name="remarks"></a>備註

此成員函式會呼叫[rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)（_ *Filename*， `_Mode` &#124; **ios_base：： in**）。 如果 open 失敗，此函式會呼叫[setstate](../standard-library/basic-ios-class.md#setstate)（ `failbit` ），這可能會擲回 ios_base：：失敗例外狀況。

### <a name="example"></a>範例

如需使用的範例，請參閱[basic_filebuf：： open](../standard-library/basic-filebuf-class.md#open) `open` 。

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream：： operator =

指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的右值。

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_ifstream` 物件的右值參考。

### <a name="return-value"></a>傳回值

傳回 **`*this`** 。

### <a name="remarks"></a>備註

成員運算子會使用*right*的內容來取代物件的內容，並將其視為右值參考。 如需詳細資訊，請參閱[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream：： rdbuf

傳回預存資料流緩衝區的位址。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>傳回值

[basic_filebuf](../standard-library/basic-filebuf-class.md) 物件的指標，表示預存的資料流緩衝區。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream：： swap

交換兩個 `basic_ifstream` 物件的內容。

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>參數

*再*\
對另一個資料流緩衝區的參考。

### <a name="remarks"></a>備註

成員函式會將此物件的內容與*右邊*的內容交換。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
