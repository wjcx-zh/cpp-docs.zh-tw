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
ms.openlocfilehash: ebf9b87b60cf790a2ca032eb805095f277324178
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416778"
---
# <a name="basic_stringstream-class"></a>basic_stringstream 類別

描述一個物件，該物件可控制如何使用 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區來插入及擷取元素和編碼物件。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>參數

配置\
配置器類別。

*Elem*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

類別樣板所描述的物件，可控制如何使用類別的資料流程緩衝區（ [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**，`Alloc`>）來插入和解壓縮元素和編碼物件，其字元特性是由類別 `Elem`所決定，而其元素是由類別 `Tr`的配置器所配置。`Alloc` 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_stringstream](#basic_stringstream)|建構類型 `basic_stringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|這個類型與樣板參數 `Alloc`同義。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[rdbuf](#rdbuf)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>。|
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|

## <a name="requirements"></a>需求

**標頭：** \<sstream >

**命名空間:** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

這個類型與樣板參數 `Alloc`同義。

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

第一個函式會藉由呼叫[basic_iostream](../standard-library/basic-iostream-class.md)（ **sb**）來初始化基類，其中 `sb` 是[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**、 **Tr**、`Alloc`> 之類別的預存物件。 它也會藉由呼叫 basic_stringbuf < **Elem**、 **Tr**、`Alloc`> （`_Mode`）來初始化 `sb`。

第二個建構函式會藉由呼叫 basic_iostream( **sb**) 初始化基底類別。 它也會藉由呼叫 basic_stringbuf < **Elem**、 **Tr**、`Alloc`> （_ *Str*、`_Mode`）來初始化 `sb`。

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

將 **pointer** 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

類型的已儲存資料流程緩衝區的位址，`pointer` 為 basic_stringbuf < **Elem**、 **Tr**、`Alloc`>。

### <a name="example"></a>範例

如需使用 [ 的範例，請參閱 ](../standard-library/basic-filebuf-class.md#close)basic_filebuf:: close`rdbuf`。

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

如需使用 `str`的範例，請參閱[basic_stringbuf：： str](../standard-library/basic-stringbuf-class.md#str) 。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
