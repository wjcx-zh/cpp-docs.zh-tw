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
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376809"
---
# <a name="basic_istringstream-class"></a>basic_istringstream 類別

描述一個物件,它控制從類[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr**>**Tr**`Alloc`的流緩衝區提取元素和編碼物件。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Alloc*\
配置器類別。

*埃萊姆*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

類範本描述一個物件,該物件控制從類[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr、>**`Alloc`的流緩衝**Tr**區中提取 元素和編碼物件,該物件具有*Elem*類型的元素,其字元特徵由類*Tr*確定,其元素由類*Alloc*的分配器分配。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

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
|[rdbuf](#rdbuf)|`pointer`將類型的存儲流緩衝區的位址返回[到basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`,>。 `Tr` `Alloc`|
|[Str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|
|[交換](#swap)|用所提供物件的值交換這個 `basic_istringstream` 物件中的值。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|從物件參數將值指派給這個 `basic_istringstream` 物件。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream:allocator_type

此類型是樣板參數 `Alloc` 的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream:basic_istringstream

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

第一個構造函數通過調用[basic_istream](../standard-library/basic-istream-class.md)`sb`()`sb`初始化基 類,其中類`Tr``Alloc`[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`的存儲物件>。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第二個建構函式會藉由呼叫 `basic_istream(sb)` 初始化基底類別。 它也會藉由呼叫 `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`) 初始化 `sb`。

第三個構造函數用*右側*的內容初始化物件,作為rvalue引用處理。

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::操作員*

從物件參數將值指派給這個 `basic_istringstream` 物件。

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>參數

*對*\
`basic_istringstream` 物件的右值參考。

### <a name="remarks"></a>備註

成員運算符將物件的內容替換為*右側*的內容,視為 rvalue 引用移動賦值。

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

`pointer`將存儲的流緩衝區的位址返回elem、Tr、>basic_stringbuf。 **Tr** `Alloc` [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

`pointer`存儲的流緩衝區的位址,< **Elem**<,tr ** **>basic_stringbuf。 `Alloc`

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream:斯特

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::交換

交換兩個 `basic_istringstream` 物件的值。

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*對*|`basic_istringstream` 物件的 `lvalue` 參考。|

### <a name="remarks"></a>備註

成員函數交換此物件的值和*右*的值。

## <a name="see-also"></a>另請參閱

[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[電流程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
