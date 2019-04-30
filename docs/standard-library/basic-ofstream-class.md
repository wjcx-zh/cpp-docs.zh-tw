---
title: basic_ofstream 類別
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: 9a8255a02c46a4ade33bd95635516e5d36fe8e64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409794"
---
# <a name="basicofstream-class"></a>basic_ofstream 類別

描述一個物件，該物件可控制如何將元素和編碼物件插入具有 `Elem` 類型元素之 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 類別的資料流緩衝區；其中該類型的字元特性是由 `Tr` 類別所決定。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Elem*<br/>
檔案緩衝區的基本項目。

*Tr*<br/>
檔案緩衝區之基本元素的特性 (通常是 `char_traits`< `Elem`>)。

## <a name="remarks"></a>備註

當**wchar_t**的特製化`basic_ofstream`寫入檔案，如果在文字模式中開啟檔案，則它會寫入 MBCS 序列。 此內部表示法將使用 `wchar_t` 字元的緩衝區。

此物件會儲存 `basic_filebuf`< `Elem`, `Tr`> 類別的物件。

## <a name="example"></a>範例

下列範例會示範如何建立 `basic_ofstream` 物件並寫入文字。

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_ofstream](#basic_ofstream)|建立 `basic_ofstream` 類型的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[close](#close)|關閉檔案。|
|[is_open](#is_open)|判斷檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[rdbuf](#rdbuf)|傳回預存資料流緩衝區的位址。|
|[swap](#swap)|將這個 `basic_ofstream` 的內容和提供的 `basic_ofstream` 內容交換。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的 `rvalue reference`。|

## <a name="requirements"></a>需求

**標頭：**\<fstream>

**命名空間：** std

## <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream

建立 `basic_ofstream` 類型的物件。

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>參數

*_Filename*<br/>
要開啟之檔案的名稱。

*_Mode*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*_Prot*<br/>
預設檔案開啟保護，相當於 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 參數。

*right*<br/>
正在用來初始化此 `basic_ofstream` 物件之 `basic_ofstream` 物件的右值參考。

### <a name="remarks"></a>備註

第一個建構函式初始化基底類別，藉由呼叫[basic_ostream](../standard-library/basic-ostream-class.md)(`sb`)，其中`sb`是類別的預存的物件[basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem`， `Tr`>。 它也會藉由呼叫 `basic_filebuf`< `Elem`, `Tr`> 初始化 `sb`。

第二個和第三個建構函式會藉由呼叫 `basic_ostream`( **sb**) 初始化基底類別。 它也會初始化`sb`藉由呼叫`basic_filebuf` <  `Elem`， `Tr`>，然後`sb`。 [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`)。 如果第二個函式會傳回 null 指標，建構函式會呼叫[setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`)。

第四個建構函式是複製函式。 它會初始化物件的內容*右*，視為右值參考。

### <a name="example"></a>範例

下列範例會示範如何建立 `basic_ofstream` 物件並寫入文字。

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="close"></a>  basic_ofstream::close

關閉檔案。

```cpp
void close();
```

### <a name="remarks"></a>備註

成員函式呼叫[rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[關閉](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>範例

如需使用 `close` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="is_open"></a>  basic_ofstream::is_open

指出檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

若已開啟檔案，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

此成員函式會傳回[rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>範例

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="open"></a>  basic_ofstream::open

開啟檔案。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>參數

*_Filename*<br/>
要開啟之檔案的名稱。

*_Mode*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*_Prot*<br/>
預設檔案開啟保護，相當於 [_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 中的 `shflag` 參數。

### <a name="remarks"></a>備註

此成員函式會呼叫 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *檔名*, `_Mode` &#124; `ios_base::out`)。 如果該函式會傳回 null 指標，函式會呼叫[setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`)。

### <a name="example"></a>範例

請參閱[basic_filebuf:: open](../standard-library/basic-filebuf-class.md#open)如需範例，會使用`open`。

## <a name="op_eq"></a>  basic_ofstream::operator=

指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的 `rvalue reference`。

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>參數

*right*<br/>
`basic_ofstream` 物件的右值參考。

### <a name="return-value"></a>傳回值

傳回 `*this`。

### <a name="remarks"></a>備註

成員運算子會取代物件的內容使用的內容*右*，視為右值參考。

## <a name="rdbuf"></a>  basic_ofstream::rdbuf

傳回預存資料流緩衝區的位址。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>傳回值

傳回預存資料流緩衝區的位址。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="swap"></a>  basic_ofstream::swap

交換兩個 `basic_ofstream` 物件的內容。

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>參數

*right*<br/>
對其他 `basic_ofstream` 物件的 `lvalue` 參考。

### <a name="remarks"></a>備註

此成員函式交換的內容，此物件的內容*右*。

## <a name="see-also"></a>另請參閱

[basic_ostream 類別](../standard-library/basic-ostream-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
