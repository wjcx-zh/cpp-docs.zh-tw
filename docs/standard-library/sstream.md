---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 6ab2164e4969a2320f67d479062808b33b0869f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212133"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

定義數個類別樣板，支援在配置的陣列物件中儲存的序列上進行 iostreams 作業。 這類序列可以輕鬆地在類別樣板[basic_string](../standard-library/basic-string-class.md)的物件之間來回轉換。

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

|參數|說明|
|---------------|-----------------|
|*左面*|`sstream` 物件的參考。|
|*再*|`sstream` 物件的參考。|

## <a name="remarks"></a>備註

類型的物件 `char *` 可以使用中的功能 [\<strstream>](../standard-library/strstream.md) 來進行資料流程處理。 不過，\<strstream> 已被取代，建議使用 \<sstream>。

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|建立樣板 `basic_istringstream` 參數上特製化的類型 **`char`** 。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|建立樣板 `basic_ostringstream` 參數上特製化的類型 **`char`** 。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|建立樣板 `basic_stringbuf` 參數上特製化的類型 **`char`** 。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|建立樣板 `basic_stringstream` 參數上特製化的類型 **`char`** 。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|建立樣板 `basic_istringstream` 參數上特製化的類型 **`wchar_t`** 。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|建立樣板 `basic_ostringstream` 參數上特製化的類型 **`wchar_t`** 。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|建立樣板 `basic_stringbuf` 參數上特製化的類型 **`wchar_t`** 。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|建立樣板 `basic_stringstream` 參數上特製化的類型 **`wchar_t`** 。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[調換](../standard-library/sstream-functions.md#sstream_swap)|在 `sstream` 物件之間交換值。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與陣列物件中儲存的項目序列之間的往來傳輸。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述一個物件，它會從類別的資料流程緩衝區中控制專案和編碼物件的解壓縮[basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**， **Tr**， `Alloc`>，其中的 `Elem` 字元特性是由類別所決定 `Tr` ，而其元素是由類別 `Alloc` 的配置器所配置。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述的物件可控制如何將元素和編碼物件插入至類別的資料流程緩衝區， [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **Elem**、 **Tr**、 `Alloc`>，以及類型的元素 `Elem` ，其字元特性是由類別所決定 `Tr` ，且其元素是由類別 `Alloc` 的配置器所配置。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述一個物件，它會使用類別的資料流程緩衝區（ [basic_stringbuf](../standard-library/basic-stringbuf-class.md)Elem，Tr，>）來控制專案和已編碼物件的插入和解壓縮 < **Elem** **Tr** `Alloc` ， `Elem` 其字元特性是由類別所決定 `Tr` ，而且其元素是由類別 `Alloc` 的配置器所配置。|

## <a name="requirements"></a>需求

- **標頭：**\<sstream>

- **命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
