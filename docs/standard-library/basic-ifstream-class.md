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
ms.openlocfilehash: 85a315ee393a002da4d0999569d4af6c34a37ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376836"
---
# <a name="basic_ifstream-class"></a>basic_ifstream 類別

描述一個物件,它控制從類[basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`的流緩衝區中提取元素和編碼物件,>,`Tr`其元素`Elem`的類型`Tr`由類 確定。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>參數

*埃萊姆*\
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

|建構函式|描述|
|-|-|
|[basic_ifstream](#basic_ifstream)|初始化 `basic_ifstream` 物件的新執行個體。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[關閉](#close)|關閉檔案。|
|[is_open](#is_open)|判斷檔案是否為開啟。|
|[open](#open)|開啟檔案。|
|[rdbuf](#rdbuf)|傳回預存資料流緩衝區的位址。|
|[交換](#swap)|將此 `basic_ifstream` 的內容和提供的 `basic_ifstream` 內容交換。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的 `rvalue`。|

## <a name="requirements"></a>需求

**標頭：** \<fstream>

**命名空間：** std

## <a name="basic_ifstreambasic_ifstream"></a><a name="basic_ifstream"></a>basic_ifstream::basic_ifstream

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

第一個構造函數通過調用[basic_istream](../standard-library/basic-istream-class.md) `sb`() 初始`sb`化基類 ,其中類`Tr`[basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`的存儲物件>。 它也會藉由呼叫 `basic_filebuf`< `Elem`, `Tr`> 初始化 `sb`。

第二個和第三個建構函式會藉由呼叫 `basic_istream`( `sb`) 初始化基底類別。 它還`sb`通過調用basic_filebuf,>,[basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem``Tr`然後`sb`初始化。 [打開](../standard-library/basic-filebuf-class.md#open)`_Filename` `ios_base::in`(, `_Mode` &#124; )。 如果後一個函數傳回空指標,則建構函數將呼叫**setstate**( `failbit`。

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

## <a name="basic_ifstreamclose"></a><a name="close"></a>basic_ifstream:關閉

關閉檔案。

```cpp
void close();
```

### <a name="remarks"></a>備註

成員函數呼叫[rdbuf](#rdbuf) **->** [關閉](../standard-library/basic-filebuf-class.md#close)。

### <a name="example"></a>範例

如需使用 `close` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ifstreamis_open"></a><a name="is_open"></a>basic_ifstream:is_open

判斷檔案是否為開啟。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>傳回值

若已開啟檔案，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

成員函數傳回[rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)。

### <a name="example"></a>範例

如需使用 `is_open` 的範例，請參閱 [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)。

## <a name="basic_ifstreamopen"></a><a name="open"></a>basic_ifstream::打開

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

成員函數呼叫[rdbuf](#rdbuf) **->** `_Mode`[開啟](../standard-library/basic-filebuf-class.md#open)(**檔案名稱*,&#124;ios_base::in 。 **ios_base::in** 如果打開失敗,函數將調用[setstate](../standard-library/basic-ios-class.md#setstate)(`failbit`),這可能會引發ios_base:失敗異常。

### <a name="example"></a>範例

有關使用`open`的範例,請參閱[basic_filebuf::打開](../standard-library/basic-filebuf-class.md#open)。

## <a name="basic_ifstreamoperator"></a><a name="op_eq"></a>basic_ifstream::操作員*

指派此資料流物件的內容。 這是一個移動指派，涉及不會留下複本的右值。

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_ifstream` 物件的右值參考。

### <a name="return-value"></a>傳回值

傳回 `*this`。

### <a name="remarks"></a>備註

成員運算符使用*權利*的內容替換物件的內容,該內容被視為rvalue引用。 如需詳細資訊，請參閱[左值和右值](../cpp/lvalues-and-rvalues-visual-cpp.md)。

## <a name="basic_ifstreamrdbuf"></a><a name="rdbuf"></a>basic_ifstream::rdbuf

傳回預存資料流緩衝區的位址。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>傳回值

[basic_filebuf](../standard-library/basic-filebuf-class.md) 物件的指標，表示預存的資料流緩衝區。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ifstreamswap"></a><a name="swap"></a>basic_ifstream::交換

交換兩個 `basic_ifstream` 物件的內容。

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>參數

*對*\
對另一個資料流緩衝區的參考。

### <a name="remarks"></a>備註

成員函數將此物件的內容交換為*權利*的內容。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
