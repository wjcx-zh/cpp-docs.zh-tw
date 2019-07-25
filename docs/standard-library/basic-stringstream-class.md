---
title: basic_stringstream 類別
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: 9278b6ce0fa23fa875f1af57ea15719111439372
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447800"
---
# <a name="basicstringstream-class"></a>basic_stringstream 類別

描述一個物件，該物件可控制如何使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區來插入及擷取元素和編碼物件。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*配置*\
配置器類別。

*Elem*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

此樣板類別所描述的物件可控制如何使用[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`> 類別的資料流程緩衝區來插入和解壓縮專案和編碼物件, 並以類型為的元素`Elem`, 其字元特性是由類別`Tr`所決定, 且其元素是由類別`Alloc`的配置器所配置。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_stringstream](#basic_stringstream)|建構類型 `basic_stringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|此類型是範本參數 `Alloc`的同義字。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[rdbuf](#rdbuf)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>。|
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

此類型是範本參數 `Alloc`的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

建構類型 `basic_stringstream` 的物件。

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*str*\
`basic_string` 類型的物件。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫[basic_iostream](../standard-library/basic-iostream-class.md)( **sb**) 來初始化基類`sb` , 其中是[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`> 類別的預存物件。 它也會`sb`藉由呼叫 basic_stringbuf < **Elem**、 **Tr** `Alloc`> ( `_Mode`) 來初始化。

第二個建構函式會藉由呼叫 basic_iostream( **sb**) 初始化基底類別。 它也會`sb`藉由呼叫 basic_stringbuf < **Elem**、 **Tr** `Alloc`> (_ *Str*, `_Mode`) 來初始化。

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

將 **pointer** 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

`pointer`要 basic_stringbuf 之類型的已儲存資料流程緩衝區的位址 < **Elem**、 **Tr** `Alloc`>。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_stringstream::str

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

傳回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函式會呼叫 `rdbuf` -> **str**( `_Newstr`)。

### <a name="example"></a>範例

如需使用`str`的範例, 請參閱[basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str) 。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
