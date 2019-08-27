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
ms.openlocfilehash: 685195b13960c325076f1a38461394ada374d4b1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452539"
---
# <a name="basicistringstream-class"></a>basic_istringstream 類別

描述一個物件，該物件可控制如何從 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區擷取元素和編碼物件。

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

此樣板類別描述一個物件, 它會從[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`> 類別的資料流程緩衝區中, 控制專案和編碼物件的提取, 以及*Elem*類型的元素。其字元特性取決於類別*Tr*, 而且其元素是由類別配置的配置器所配置。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_istringstream](#basic_istringstream)|建構類型 `basic_istringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[allocator_type](#allocator_type)|此類型是範本參數 `Alloc`的同義字。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[rdbuf](#rdbuf)|將 `pointer` 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>。|
|[str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|
|[swap](#swap)|用所提供物件的值交換這個 `basic_istringstream` 物件中的值。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|從物件參數將值指派給這個 `basic_istringstream` 物件。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

此類型是範本參數 `Alloc`的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

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

*str*\
`basic_string` 類型的物件。

*再*\
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

第一個函式會藉由呼叫[basic_istream](../standard-library/basic-istream-class.md)(`sb`) 來初始化基類`sb` , 其中是[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`、 `Tr` `Alloc`> 類別的預存物件. 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第二個建構函式會藉由呼叫 `basic_istream(sb)` 初始化基底類別。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第三個函式會使用*right*的內容初始化物件, 並將其視為右值參考。

## <a name="op_eq"></a>  basic_istringstream::operator=

從物件參數將值指派給這個 `basic_istringstream` 物件。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>參數

*再*\
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

成員運算子會以*right*的內容取代物件的內容, 並將其視為右值參考移動指派。

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

`pointer`將類型之儲存資料流程緩衝區的位址傳回[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

`pointer`要 basic_stringbuf 之類型的已儲存資料流程緩衝區的位址 < **Elem**、 **Tr** `Alloc`>。

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="str"></a>  basic_istringstream::str

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

## <a name="swap"></a>  basic_istringstream::swap

交換兩個 `basic_istringstream` 物件的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*right*|`basic_istringstream` 物件的 `lvalue` 參考。|

### <a name="remarks"></a>備註

此成員函式會交換這個物件的值和*right*的值。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
