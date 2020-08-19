---
title: basic_istringstream 類別
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: fd2ab79466c01343cbdadbcb649e3b05eee3c2a0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561774"
---
# <a name="basic_istringstream-class"></a>basic_istringstream 類別

描述一個物件，該物件會從類別的資料流程緩衝區中，控制專案和編碼物件的解壓縮[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**、 **Tr**、 `Alloc`>。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>參數

*配置*\
配置器類別。

*Elem*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

類別樣板描述的物件可控制如何從類別的資料流程緩衝區中，將專案和編碼物件的解壓縮[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**、 **Tr**、 `Alloc`>，以及*Elem*類型的元素，其字元特性是由類別*Tr*所決定，而其元素是由類別配置的*Alloc*配置器所配置。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_istringstream](#basic_istringstream)|建構類型 `basic_istringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|此類型是樣板參數 `Alloc` 的同義字。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[rdbuf](#rdbuf)|傳回 `pointer` 要[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` 、 `Tr` 、 `Alloc`> 之預存資料流程緩衝區的位址。|
|[Str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|
|[交換](#swap)|用所提供物件的值交換這個 `basic_istringstream` 物件中的值。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子 =](#op_eq)|從物件參數將值指派給這個 `basic_istringstream` 物件。|

## <a name="requirements"></a>規格需求

**標頭：**\<sstream>

**命名空間：** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a> basic_istringstream：： allocator_type

此類型是樣板參數 `Alloc` 的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a> basic_istringstream：： basic_istringstream

建構類型 `basic_istringstream` 的物件。

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>參數

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*Str*\
`basic_string` 類型的物件。

*對*\
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫[basic_istream](../standard-library/basic-istream-class.md) () 來初始化基類 `sb` ，其中 `sb` 是類別的預存物件[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` 、 `Tr` ， `Alloc`>。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第二個建構函式會藉由呼叫 `basic_istream(sb)` 初始化基底類別。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第三個函式會以 *right*的內容初始化物件，並將其視為右值參考。

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a> basic_istringstream：： operator =

從物件參數將值指派給這個 `basic_istringstream` 物件。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

成員運算子會以 *right*的內容取代物件的內容，並將其視為右值參考移動指派。

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a> basic_istringstream：： rdbuf

傳回類型的預存資料流程緩衝區的位址 `pointer` ，以[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**、 **Tr**、 `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

`pointer`要 basic_stringbuf< **Elem**、 **Tr**、> 之預存資料流程緩衝區的位址 `Alloc` 。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_istringstreamstr"></a><a name="str"></a> basic_istringstream：： str

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

傳回類別的物件[basic_string](../standard-library/basic-string-class.md) <  **Elem**， **Tr**， `Alloc`>，其受控制的序列是** \* 由此**所控制之序列的複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回[rdbuf](#rdbuf)  ->  [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函式會呼叫 `rdbuf`  ->  **str** ( `_Newstr`) 。

### <a name="example"></a>範例

如需使用的範例，請參閱 [basic_stringbuf：： str](../standard-library/basic-stringbuf-class.md#str) `str` 。

## <a name="basic_istringstreamswap"></a><a name="swap"></a> basic_istringstream：： swap

交換兩個 `basic_istringstream` 物件的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_istringstream` 物件的 lvalue 參考。

### <a name="remarks"></a>備註

成員函式會交換這個物件的值和 *右邊*的值。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
