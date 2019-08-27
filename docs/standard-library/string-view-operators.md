---
title: '&lt;string_view&gt;運算子'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: caa6e515428cc0ea767eef20e819753c8f7ff8f9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459225"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt;運算子

使用這些運算子來比較兩個 string_view 物件, 或是提供隱含轉換的 string_view 和一些其他字串物件 (例如[std:: string](basic-string-class.md)或**char\*** )。 

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operator""sv](#op_sv)|

## <a name="op_neq"></a>operator! =

測試運算子左邊的物件是否不等於右邊的物件。

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件未詞典編纂等於右邊的物件,**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

隱含轉換必須存在於*convertible_string_type*到另一端的 string_view。 

比較是以字元序列的成對字典比較為基礎。 如果它們有相同數目的元素, 且元素全都相等, 則兩個物件相等。 反之則為不相等。

## <a name="op_eq_eq"></a>operator = =

測試運算子左邊的物件是否等於右邊的物件。

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件詞典編纂等於右邊的物件,**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

隱含轉換必須存在於*convertible_string_type*到另一端的 string_view。 

比較是以字元序列的成對字典比較為基礎。 如果它們有相同數目的元素, 且元素全都相等, 則兩個物件相等。


## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的物件是否小於右邊 sidestring_view 的物件。
```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件詞典編纂小於右邊的物件, 則**為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

隱含轉換必須存在於*convertible_string_type*到另一端的 string_view。 

比較是以字元序列的成對字典比較為基礎。 遇到第一組不相等的字元時, 會傳回該比較的結果。 如果找不到不相等的字元, 但有一個序列較短, 則較短的順序會小於較長的序列。 換句話說, 「貓」小於「貓」。

### <a name="example"></a>範例

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的物件是否小於或等於右邊的物件。

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件詞典編纂小於或等於右邊的物件,**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

請[參閱&lt;運算子](#op_lt)。

## <a name="op_lt_lt"></a>操作&lt;&lt;

將 string_view 寫入輸出資料流程。

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>參數

*Ostr*\
要寫入的輸出資料流程。

*Str*\
要輸入輸出資料流程的 string_view。

### <a name="return-value"></a>傳回值

要寫入的輸出資料流程。

### <a name="remarks"></a>備註

使用此運算子將 string_view 的內容插入輸出資料流程中, 例如使用[std:: cout](iostream.md#cout)。

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的物件是否大於右邊的物件。

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件詞典編纂大於右邊的 string_view 物件, 則**為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

請[參閱&lt;運算子](#op_lt)。

## <a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的物件是否大於或等於右邊的物件。

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*左面*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

*再*\
要比較的任何可轉換字串類型或`basic_string_view`類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的物件詞典編纂大於或等於右邊的物件,**則為 true** ;否則**為 false**。

### <a name="remarks"></a>備註

請[參閱&lt;運算子](#op_lt)。

## <a name="op_sv"></a>運算子 "" sv (string_view 常值)

從字串常值中 string_view。 需要命名`std::literals::string_view_literals`空間。 

### <a name="example"></a>範例

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>另請參閱

[\<string_view>](../standard-library/string-view.md)
