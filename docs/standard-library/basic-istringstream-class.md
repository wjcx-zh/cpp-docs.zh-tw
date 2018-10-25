---
title: basic_istringstream 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs:
- C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca24c555373b1ae9c09bb8c35daaffe61768813
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062986"
---
# <a name="basicistringstream-class"></a>basic_istringstream 類別

描述一個物件，該物件可控制如何從 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`> 類別的資料流緩衝區擷取元素和編碼物件。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>參數

*配置*<br/>
配置器類別。

*Elem*<br/>
字串之基本項目的類型。

*Tr*<br/>
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

此範本類別描述的物件可控制擷取元素和編碼的物件類別的資料流緩衝區[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**， `Alloc`>，類型的項目*Elem*，其字元特性由類別*Tr*，且其項目會配置器所配置類別*配置*。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_istringstream](#basic_istringstream)|建構類型 `basic_istringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
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

**標頭︰**\<sstream>

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

*模式 （_m)*<br/>
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*str*<br/>
`basic_string` 類型的物件。

*right*<br/>
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

第一個建構函式初始化基底類別，藉由呼叫[basic_istream](../standard-library/basic-istream-class.md)(`sb`)，其中`sb`是類別的預存的物件[basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`， `Tr`， `Alloc`>。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第二個建構函式會藉由呼叫 `basic_istream(sb)` 初始化基底類別。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第三個建構函式初始化物件的內容*右*，視為右值參考。

## <a name="op_eq"></a>  basic_istringstream::operator=

從物件參數將值指派給這個 `basic_istringstream` 物件。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>參數

*right*<br/>
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

此成員運算子會將物件的內容取代的內容*右*，視為右值參考移動指派。

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

傳回類型的預存資料流緩衝區的位址`pointer`要[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**， **Tr**， `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

類型的預存資料流緩衝區的位址`pointer`basic_stringbuf < **Elem**， **Tr**， `Alloc`>。

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

*_Newstr*<br/>
新字串。

### <a name="return-value"></a>傳回值

傳回 [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> 類別的物件，其受控制的序列是由 **\*this** 所控制的序列複本。

### <a name="remarks"></a>備註

第一個成員函式會傳回 [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函式會呼叫 `rdbuf` -> **str**( `_Newstr`)。

### <a name="example"></a>範例

請參閱[basic_stringbuf:: str](../standard-library/basic-stringbuf-class.md#str)如需範例，會使用`str`。

## <a name="swap"></a>  basic_istringstream::swap

交換兩個 `basic_istringstream` 物件的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*right*|`basic_istringstream` 物件的 `lvalue` 參考。|

### <a name="remarks"></a>備註

成員函式會交換這個物件的值和值*右*。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
