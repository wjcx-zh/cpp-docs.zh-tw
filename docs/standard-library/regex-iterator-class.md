---
title: regex_iterator 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: d9d2baf99b1e2334132f54aeace3d8197b1e73da
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217580"
---
# <a name="regex_iterator-class"></a>regex_iterator 類別

相符項目的迭代器類別。

## <a name="syntax"></a>語法

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>參數

*BidIt*\
子相符項目的迭代器類型。

*Elem*\
要符合之項目的類型。

*RXtraits*\
項目的 Traits 類別。

## <a name="remarks"></a>備註

類別範本會描述常數正向反覆運算器物件。 它會將其規則運算式物件 `match_results<BidIt>` 重複套用至迭代器範圍 `*pregex` 所定義的字元序列，藉以擷取 `[begin, end)`類型的物件。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[regex_iterator](#regex_iterator)|建構迭代器。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[difference_type](#difference_type)|迭代器差值的類型。|
|[iterator_category](#iterator_category)|迭代器分類的類型。|
|[滑鼠](#pointer)|要比對的指標類型。|
|[reference](#reference)|對應的參考類型。|
|[RegEx_type](#regex_type)|要比對的規則運算式類型。|
|[value_type](#value_type)|相符項目的類型。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator！ =](#op_neq)|比較迭代器是否不相等。|
|[操作](#op_star)|存取指定的相符項目。|
|[operator + +](#op_add_add)|遞增迭代器。|
|[operator =](#op_eq)|比較迭代器是否相等。|
|[operator->](#op_arrow)|存取指定的相符項目。|

## <a name="requirements"></a>需求

**標頭：**\<regex>

**命名空間：** std

## <a name="examples"></a>範例

如需規則運算式的相關範例，請參閱下列主題：

- [RegEx_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [調換](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a>RegEx_iterator：:d ifference_type

迭代器差值的類型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>備註

這個類型與 `std::ptrdiff_t`同義。

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a>RegEx_iterator：： iterator_category

迭代器分類的類型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>備註

這個類型與 `std::forward_iterator_tag`同義。

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a>RegEx_iterator：： operator！ =

比較迭代器是否不相等。

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>參數

*再*\
要比較的迭代器。

### <a name="remarks"></a>備註

成員函式會傳回 `!(*this == right)`。

## <a name="regex_iteratoroperator"></a><a name="op_star"></a>RegEx_iterator：： operator *

存取指定的相符項目。

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>備註

成員函式會傳回儲存的值 `match`。

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a>RegEx_iterator：： operator + +

遞增迭代器。

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>備註

如果目前比對沒有任何字元，第一個運算子會呼叫 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`；否則會前進到儲存值 `begin` ，以指向目前比對之後的第一個字元，再呼叫 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`。 不論是哪種情況，如果搜尋失敗，此運算子便會將物件設定為結束序列 (end-of-sequence) 迭代器。 此運算子會傳回該物件。

第二個運算子會複製物件、遞增物件，然後傳回複本。

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a>RegEx_iterator：： operator =

比較迭代器是否相等。

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>參數

*再*\
要比較的迭代器。

### <a name="remarks"></a>備註

如果 **`*this`** 和*right*都是序列結尾反覆運算器，或如果兩者都不是序列結尾反覆運算器和、、和，則成員函式會傳回 true `begin == right.begin` `end == right.end` `pregex == right.pregex` `flags == right.flags` 。 否則會傳回 false。

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a>RegEx_iterator：： operator-&gt;

存取指定的相符項目。

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存值 `match`的位址。

## <a name="regex_iteratorpointer"></a><a name="pointer"></a>RegEx_iterator：:p ointer

要比對的指標類型。

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>*`同義，其中 `BidIt` 是範本參數。

## <a name="regex_iteratorreference"></a><a name="reference"></a>RegEx_iterator：： reference

對應的參考類型。

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>&`同義，其中 `BidIt` 是範本參數。

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a>RegEx_iterator：： RegEx_iterator

建構迭代器。

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>參數

*頭*\
要比對的序列開頭。

*次*\
要比對的序列結尾。

*重新*\
比對的規則運算式。

*f*\
比對的旗標。

### <a name="remarks"></a>備註

第一個建構函式會建構結束序列 (end-of-sequence) 迭代器。 第二個函式會 `begin` 使用*first*、預存值（ `end` *最後一個*）、儲存的值和儲存的值（含 `pregex` `&re` `flags` *f*）來初始化預存值。 然後呼叫 `regex_search(begin, end, match, *pregex, flags)`。 如果搜尋失敗，此運算子便會將物件設定為結束序列迭代器。

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a>RegEx_iterator：： RegEx_type

要比對的規則運算式類型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `basic_regex<Elem, RXtraits>`的同義字。

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a>RegEx_iterator：： value_type

相符項目的類型。

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>`同義，其中 `BidIt` 是範本參數。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[RegEx_constants 類別](../standard-library/regex-constants-class.md)\
[RegEx_error 類別](../standard-library/regex-error-class.md)\
[\<regex>函式](../standard-library/regex-functions.md)\
[RegEx_iterator 類別](../standard-library/regex-iterator-class.md)\
[\<regex>人員](../standard-library/regex-operators.md)\
[RegEx_token_iterator 類別](../standard-library/regex-token-iterator-class.md)\
[RegEx_traits 類別](../standard-library/regex-traits-class.md)\
[\<regex>typedef](../standard-library/regex-typedefs.md)
