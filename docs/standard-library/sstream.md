---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: cc08fb426df289b3478ad9d29b03f9a6dd5d3978
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605566"
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

`char *` 類型的物件可以使用 [\<strstream>](../standard-library/strstream.md) 中的功能進行串流處理。 不過， \<strstream > 已被取代，以及善用\<sstream > 建議您。

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|建立類型`basic_istringstream`特殊化**char**樣板參數。|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|建立類型`basic_ostringstream`特殊化**char**樣板參數。|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|建立類型`basic_stringbuf`特殊化**char**樣板參數。|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|建立類型`basic_stringstream`特殊化**char**樣板參數。|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|建立類型`basic_istringstream`特殊化**wchar_t**樣板參數。|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|建立類型`basic_ostringstream`特殊化**wchar_t**樣板參數。|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|建立類型`basic_stringbuf`特殊化**wchar_t**樣板參數。|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|建立類型`basic_stringstream`特殊化**wchar_t**樣板參數。|

### <a name="manipulators"></a>操作工具

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|在 `sstream` 物件之間交換值。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|描述資料流緩衝區，其控制類型 `Elem` 的項目 (其字元特性由類別 `Tr` 所決定)，與陣列物件中儲存的項目序列之間的往來傳輸。|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|描述的物件可控制擷取元素和編碼的物件類別的資料流緩衝區[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，類型的項目`Elem`，其字元特性由類別`Tr`，和其項目由類別配置器配置`Alloc`。|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|描述的物件可控制將項目和編碼的物件類別的資料流緩衝區[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，類型的項目`Elem`，其字元特性由類別`Tr`，和其項目由類別配置器配置`Alloc`。|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|描述的物件可控制插入及擷取項目和編碼的物件，使用類別的資料流緩衝區[basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**Elem**， **Tr**， `Alloc`>，類型的項目`Elem`，其字元特性由類別`Tr`，和其項目由類別配置器配置`Alloc`。|

## <a name="requirements"></a>需求

- **標頭︰**\<sstream>

- **命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
