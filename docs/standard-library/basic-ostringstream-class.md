---
title: basic_ostringstream 類別
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 45a7eb1384c70b488e057fb9df8ad4c496272316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582764"
---
# <a name="basicostringstream-class"></a>basic_ostringstream 類別

描述一個物件，該物件可控制如何將元素和編碼物件插入 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*配置*<br/>
配置器類別。

*Elem*<br/>
字串之基本項目的類型。

*Tr*<br/>
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

此類別描述的物件可控制插入的項目和編碼的物件的資料流緩衝區，類型的項目`Elem`，其字元特性由類別`Tr`，且其項目會配置器所配置類別`Alloc`。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|建構類型 `basic_ostringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|類型是範本參數的同義字*Alloc*。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[rdbuf](#rdbuf)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>。|
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|

## <a name="requirements"></a>需求

**標頭︰**\<sstream>

**命名空間：** std

## <a name="allocator_type"></a>  basic_ostringstream::allocator_type

類型是範本參數的同義字*Alloc*。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream

建構 basic_ostringstream 類型的物件。

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>參數

*模式 （_m)*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*str*<br/>
`basic_string` 類型的物件。

### <a name="remarks"></a>備註

第一個建構函式初始化基底類別，藉由呼叫[basic_ostream](../standard-library/basic-ostream-class.md)( **sb**)，其中`sb`是類別的預存的物件[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**， **Tr**， `Alloc`>。 它也會藉由呼叫 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`) 初始化 **sb**。

第二個建構函式會藉由呼叫 basic_ostream( **sb**) 初始化基底類別。 它也會初始化`sb`藉由呼叫 basic_stringbuf< < **Elem**， **Tr**， `Alloc`> (_ *Str*， `_Mode` &#124; `ios_base::out`).

## <a name="rdbuf"></a>  basic_ostringstream::rdbuf

傳回類型的預存資料流緩衝區的位址`pointer`要[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**， `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

類型的預存資料流緩衝區，地址`pointer`basic_stringbuf < **Elem**， **Tr**， `Alloc`>。

### <a name="remarks"></a>備註

此成員函式會傳回類型的預存資料流緩衝區的位址`pointer`basic_stringbuf < **Elem**， **Tr**， `Alloc`>。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_ostringstream::str

設定或取得字串緩衝區中的文字，而不需要變更寫入位置。

```cpp
basic_string<Elem, Tr, Alloc> str() const;

void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>參數

*_Newstr*<br/>
新字串。

### <a name="return-value"></a>傳回值

傳回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函式會呼叫 `rdbuf` -> **str**( `_Newstr`)。

### <a name="example"></a>範例

請參閱[basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str)如需範例，會使用`str`。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
