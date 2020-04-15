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
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376853"
---
# <a name="basic_fstream-class"></a>basic_fstream 類別

描述一個物件,該物件使用類[basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`的流緩衝區控制元素和編碼物件,>,`Tr``Elem`其字元`Tr`特徵由 類 決定。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*埃萊姆*\
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

|建構函式|描述|
|-|-|
|[basic_fstream](#basic_fstream)|建構類型 `basic_fstream` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[關閉](#close)|關閉檔案。|
|[is_open](#is_open)|判斷檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[rdbuf](#rdbuf)|返回存儲的流緩衝區的位址,該類型指標指向[basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>。 `Tr`|
|[交換](#swap)|將這個物件的內容與另一個 `basic_fstream` 物件的內容交換。|

## <a name="requirements"></a>需求

**標頭：** \<fstream>

**命名空間：** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream:basic_fstream

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
預設檔案開啟保護,等效於 _fsopen 中的*shflag*參數[,_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="remarks"></a>備註

第一個構造函數通過調用[basic_iostream](../standard-library/basic-iostream-class.md)`sb`() 初始`sb`化基類 ,其中basic_filebuf **Elem、Tr** [>的类](../standard-library/basic-filebuf-class.md)\<的存儲物件。 **Tr** `sb`它還通過調用`basic_filebuf`\<**埃萊姆****,Tr>** 初始化。

第二個和第三個建構函式會藉由呼叫 `basic_iostream`( **sb**) 初始化基底類別。 `sb`它還透過調用`basic_filebuf`\<**Elem、Tr**>,然後**sb.**[打開](../standard-library/basic-filebuf-class.md#open)(=**Tr***檔名*, `_Mode`) 初始化。 如果後一個函數傳回空指標,則建構函數將呼叫[setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`。

第四個建構函式會使用視為右值參考的 `right` 內容初始化物件。

### <a name="example"></a>範例

如需使用 `basic_fstream` 的範例，請參閱 [streampos](../standard-library/ios-typedefs.md#streampos)。

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream:關閉

關閉檔案。

```cpp
void close();
```

### <a name="remarks"></a>備註

成員函數呼叫[rdbuf](#rdbuf) **->** [關閉](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>範例

如需如何使用 `close` 的範例，請參閱 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream:is_open

判斷檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

若已開啟檔案，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>範例

如需如何使用 `is_open` 的範例，請參閱 [basic_filebuf:: is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::打開

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
預設檔案開啟保護,等效於 _fsopen 中的*shflag*參數[,_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)。

### <a name="remarks"></a>備註

成員函數呼叫[rdbuf](#rdbuf) **->** [開啟](../standard-library/basic-filebuf-class.md#open)(=`_Mode`*檔案名稱*。 如果此函數傳回空指標,則函數將呼叫[setstate](../standard-library/basic-ios-class.md#setstate)( `failbit`。

### <a name="example"></a>範例

有關如何使用`open`的範例,請參閱[basic_filebuf::打開](../standard-library/basic-filebuf-class.md#open)。

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::操作員*

將來自指定資料流物件的內容指派給此物件。 這是一個移動指派，涉及不會留下複本的 rvalue。

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_fstream` 物件的 lvalue 參考。

### <a name="return-value"></a>傳回值

傳回 `*this`。

### <a name="remarks"></a>備註

成員運算符使用*權利*的內容替換物件的內容,該內容被視為rvalue引用。

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

將 pointer 類型之預存資料流緩衝區的位址傳回至 [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>傳回值

預存資料流緩衝區的位址。

### <a name="example"></a>範例

如需如何使用 `rdbuf` 的範例，請參閱 [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream:交換

交換兩個 `basic_fstream` 物件的內容。

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_fstream` 物件的 `lvalue` 參考。

### <a name="remarks"></a>備註

成員函數交換此物件的內容和*權利*的內容。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
