---
title: basic_fstream 類別
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 8d26d0fe0e4e4152cf05476f546b753650209dfe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459593"
---
# <a name="basic_fstream-class"></a>basic_fstream 類別

描述一個物件，該物件可控制如何使用具有 `Elem` 類型元素之 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> 類別的資料流緩衝區來插入及擷取元素和編碼物件；其中該類型的字元特性是由 `Tr` 類別所決定。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Elem*\
檔案緩衝區的基本項目。

*Tr*\
檔案緩衝區之基本元素的特性 (通常是 `char_traits`< `Elem`>)。

## <a name="remarks"></a>備註

此物件會儲存 `basic_filebuf`< `Elem`, `Tr`> 類別的物件。

> [!NOTE]
> fstream 物件的 get 指標和 put 指標彼此**相依**。 如果 get 指標移動，put 指標也會跟著移動。

## <a name="example"></a>範例

下列範例示範如何建立可從中讀取和寫入的 `basic_fstream` 物件。

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_fstream](#basic_fstream)|建構類型 `basic_fstream` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[close](#close)|關閉檔案。|
|[is_open](#is_open)|判斷檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[rdbuf](#rdbuf)|將 pointer 類型之預存資料流緩衝區的位址傳回至 [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>。|
|[swap](#swap)|將這個物件的內容與另一個 `basic_fstream` 物件的內容交換。|

## <a name="requirements"></a>需求

**標頭：** \<fstream>

**命名空間：** std

## <a name="basic_fstream"></a>  basic_fstream::basic_fstream

建構類型 `basic_fstream` 的物件。

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>參數

*_Filename*\
要開啟之檔案的名稱。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*_Prot*\
預設檔案開啟保護，相當於[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)中的*shflag*參數。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫[basic_iostream](../standard-library/basic-iostream-class.md)（`sb`）來初始化基類`sb` ，其中是[basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**， **Tr**> 類別的預存物件。 它也會`sb`藉由`basic_filebuf` \<呼叫**Elem**， **Tr**> 來初始化。

第二個和第三個建構函式會藉由呼叫 `basic_iostream`( **sb**) 初始化基底類別。 它也會`sb`藉由`basic_filebuf` \<呼叫**Elem**、 **Tr**>，然後再[開啟](../standard-library/basic-filebuf-class.md#open) **sb**（_ *Filename*， `_Mode`）來初始化。 如果後面一個函式傳回 null 指標，則此函式會`failbit`呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)（）。

第四個建構函式會使用視為右值參考的 `right` 內容初始化物件。

### <a name="example"></a>範例

如需使用 `basic_fstream` 的範例，請參閱 [streampos](../standard-library/ios-typedefs.md#streampos)。

## <a name="close"></a>  basic_fstream::close

關閉檔案。

```cpp
void close();
```

### <a name="remarks"></a>備註

此成員函式會呼叫 [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>範例

如需如何使用 `close` 的範例，請參閱 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="is_open"></a>  basic_fstream::is_open

判斷檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

若已開啟檔案，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

此成員函式會傳回 [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>範例

如需如何使用 `is_open` 的範例，請參閱 [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="open"></a>  basic_fstream::open

開啟檔案。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
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
預設檔案開啟保護，相當於[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)中的*shflag*參數。

### <a name="remarks"></a>備註

此成員函式會呼叫 [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *檔名*, `_Mode`)。 如果該函式傳回 null 指標，則函式會呼叫`failbit`[setstate](../standard-library/basic-ios-class.md#setstate)（）。

### <a name="example"></a>範例

如需如何使用`open`的範例，請參閱[basic_filebuf：： open](../standard-library/basic-filebuf-class.md#open) 。

## <a name="op_eq"></a>  basic_fstream::operator=

將來自指定資料流物件的內容指派給此物件。 這是一個移動指派，涉及不會留下複本的 rvalue。

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_fstream` 物件的 lvalue 參考。

### <a name="return-value"></a>傳回值

傳回 `*this`。

### <a name="remarks"></a>備註

成員運算子會使用*right*的內容來取代物件的內容，並將其視為右值參考。

## <a name="rdbuf"></a>  basic_fstream::rdbuf

將 pointer 類型之預存資料流緩衝區的位址傳回至 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>傳回值

預存資料流緩衝區的位址。

### <a name="example"></a>範例

如需如何使用 `rdbuf` 的範例，請參閱 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="swap"></a>  basic_fstream::swap

交換兩個 `basic_fstream` 物件的內容。

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_fstream` 物件的 `lvalue` 參考。

### <a name="remarks"></a>備註

此成員函式會交換這個物件的內容和*right*的內容。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
