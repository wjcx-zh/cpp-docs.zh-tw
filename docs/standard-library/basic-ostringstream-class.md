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
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376771"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream 類別

描述一個物件,它控制將元素和編碼的對象插入**elem、Tr** **Tr** `Alloc` [>basic_stringbuf类](../standard-library/basic-stringbuf-class.md)< 的流緩衝區中。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Alloc*\
配置器類別。

*埃萊姆*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

類描述一個物件,該物件控制將元素和編碼物件插入到流緩衝區中,其元素的類型`Elem`由`Tr`類確定,其元素由`Alloc`類的分配器分配。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|建構類型 `basic_ostringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|該類型是範本參數*Alloc*的同義詞。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[rdbuf](#rdbuf)|`pointer`將類型的存儲流緩衝區的位址返回[到basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`,>。 `Tr` `Alloc`|
|[Str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream:allocator_type

該類型是範本參數*Alloc*的同義詞。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

建構 basic_ostringstream 類型的物件。

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>參數

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*Str*\
`basic_string` 類型的物件。

### <a name="remarks"></a>備註

第一個構造函數通過調用[basic_ostream](../standard-library/basic-ostream-class.md) **(sb)**`sb`初始化基< 類,其中basic_stringbuf Elem、Tr、>basic_stringbuf`Alloc`[類的](../standard-library/basic-stringbuf-class.md)存儲物件。** ** **Tr** 它也會藉由呼叫 basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`) 初始化 **sb**。

第二個建構函式會藉由呼叫 basic_ostream( **sb**) 初始化基底類別。 `sb`它還通過調用basic_stringbuf<**埃萊姆****,Tr,>(*** `Alloc` *斯特* `_Mode` `ios_base::out` ,&#124;)。

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

`pointer`將存儲的流緩衝區的位址返回elem、Tr、>basic_stringbuf。 **Tr** `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

存儲的`pointer`流緩衝區的位址,類型為basic_stringbuf< **Elem、Tr、>。** **Tr** `Alloc`

### <a name="remarks"></a>備註

成員`pointer`函數將存儲的流緩衝區的位址返回到basic_stringbuf< **Elem、Tr、>。** **Tr** `Alloc`

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream:斯特

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

傳回類別[的資料basic_string](../standard-library/basic-string-class.md)< **Elem,** **Tr,>,**`Alloc`其受控序列是**\*受此**控制序列的副本。

### <a name="remarks"></a>備註

第一個成員函數傳回[rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str)。 第二個成員函數呼叫`rdbuf` -> **str**str `_Newstr`( 。

### <a name="example"></a>範例

有關`str`使用的示例,請參閱[basic_stringbuf::str。](../standard-library/basic-stringbuf-class.md#str)

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
