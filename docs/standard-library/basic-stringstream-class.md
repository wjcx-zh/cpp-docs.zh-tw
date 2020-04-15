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
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364875"
---
# <a name="basic_stringstream-class"></a>basic_stringstream 類別

描述一個物件,該物件使用類[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr**>**Tr**`Alloc`的流緩衝區控制元素和編碼對象的插入和提取。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>參數

*Alloc*\
配置器類別。

*埃萊姆*\
字串之基本項目的類型。

*Tr*\
字元特性是在字串的基本項目上特製化。

## <a name="remarks"></a>備註

類範本描述一個物件,該物件使用類[basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem、Tr、>****Tr**`Alloc`的流緩衝區控制元素和編碼物件的插入和提取,該流緩`Elem`衝區具有 類型元素,其字`Tr`元特徵由類 確定`Alloc`,其元素由類的分配器分配。 這個物件會儲存 basic_stringbuf< **Elem**, **Tr**, `Alloc`> 類別的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[basic_stringstream](#basic_stringstream)|建構類型 `basic_stringstream` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[allocator_type](#allocator_type)|此類型是樣板參數 `Alloc` 的同義字。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[rdbuf](#rdbuf)|`pointer`將類型的存儲流緩衝區的位址返回[到basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`,>。 `Tr` `Alloc`|
|[Str](#str)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|

## <a name="requirements"></a>需求

**標頭︰** \<sstream>

**命名空間：** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream:allocator_type

此類型是樣板參數 `Alloc` 的同義字。

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream:basic_stringstream

建構類型 `basic_stringstream` 的物件。

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>參數

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) 中的其中一個列舉。

*Str*\
`basic_string` 類型的物件。

### <a name="remarks"></a>備註

第一個構造函數通過調用[basic_iostream](../standard-library/basic-iostream-class.md) **(sb)**`sb`初始化基< 類,其中basic_stringbuf**Elem、Tr、>****Tr**`Alloc`[的類](../standard-library/basic-stringbuf-class.md)的存儲物件。 它還`sb`通過調用basic_stringbuf<**埃萊姆****,Tr,>()。** `Alloc` `_Mode`

第二個建構函式會藉由呼叫 basic_iostream( **sb**) 初始化基底類別。 它還`sb`通過調用basic_stringbuf<**埃萊姆****,Tr,>(*** `Alloc` *Str)*`_Mode`來初始化。

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

將 **pointer** 類型之預存資料流緩衝區的位址傳回至 [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>。

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>傳回值

`pointer`存儲的流緩衝區的位址,< **Elem**<,tr ** **>basic_stringbuf。 `Alloc`

### <a name="example"></a>範例

如需使用 `rdbuf` 的範例，請參閱 [basic_filebuf:: close](../standard-library/basic-filebuf-class.md#close)。

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream:斯特

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
