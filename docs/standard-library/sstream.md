---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 8284e56e8afb1e5518cbcbb772079b4f19d57b18
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451737"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

定義數個樣板類別，以便在已配置陣列物件中所儲存的序列上支援 iostreams 作業。 這類序列可在樣板類別 [basic_string](../standard-library/basic-string-class.md) 的物件之間輕鬆地來回轉換。

## <a name="syntax"></a>語法

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*left*|`sstream` 物件的參考。|
|*right*|`sstream` 物件的參考。|

## <a name="remarks"></a>備註

`char *` 類型的物件可以使用 [\<strstream>](../standard-library/strstream.md) 中的功能進行串流處理。 不過, \<strstream > 已被取代, 而且鼓勵\<使用 sstream >。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|建立在`basic_istringstream` **char**樣板參數上特製化的型別。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|建立在`basic_ostringstream` **char**樣板參數上特製化的型別。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|建立在`basic_stringbuf` **char**樣板參數上特製化的型別。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|建立在`basic_stringstream` **char**樣板參數上特製化的型別。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|建立在`basic_istringstream` **wchar_t**樣板參數上特製化的類型。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|建立在`basic_ostringstream` **wchar_t**樣板參數上特製化的類型。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|建立在`basic_stringbuf` **wchar_t**樣板參數上特製化的類型。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|建立在`basic_stringstream` **wchar_t**樣板參數上特製化的類型。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|在 `sstream` 物件之間交換值。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與陣列物件中儲存的項目序列之間的往來傳輸。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述一個物件, 它會從[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **Tr**, `Alloc`> 類別的資料流程緩衝區中, 控制專案和編碼物件的解壓縮, 並`Elem`以類型的元素 (其字元特性是由類別`Tr`所決定, 且其元素是由類別`Alloc`的配置器所配置。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述的物件可控制如何將元素和編碼物件插入[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **Tr**, `Alloc`> 類別的資料流程緩衝區中, 其中包含類型`Elem`的元素, 其字元特性為是由類別`Tr`所決定, 且其元素是由類別`Alloc`的配置器所配置。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述一個物件, 該物件會使用[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**, **Tr**, `Alloc`> 類別的資料流程緩衝區 (具有類型`Elem`的元素) 來控制插入和解壓縮元素和編碼物件, 其字元特性是由類別`Tr`所決定, 且其元素是由類別`Alloc`的配置器所配置。|

## <a name="requirements"></a>需求

- **標頭︰** \<sstream>

- **命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
