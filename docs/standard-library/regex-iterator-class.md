---
title: regex_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2502ab1d7fbcbfc33883df3627ec36dfcf46e2d7
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535336"
---
# <a name="regexiterator-class"></a>regex_iterator 類別

相符項目的迭代器類別。

## <a name="syntax"></a>語法

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator 
```

## <a name="parameters"></a>參數

*BidIt*<br/>
子相符項目的迭代器類型。

*Elem*<br/>
要符合之項目的類型。

*RXtraits*<br/>
項目的 Traits 類別。

## <a name="remarks"></a>備註

此範本類別描述常數正向迭代器物件。 它會將其規則運算式物件 `match_results<BidIt>` 重複套用至迭代器範圍 `*pregex` 所定義的字元序列，藉以擷取 `[begin, end)`類型的物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[regex_iterator](#regex_iterator)|建構迭代器。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[difference_type](#difference_type)|迭代器差值的類型。|
|[iterator_category](#iterator_category)|迭代器分類的類型。|
|[pointer](#pointer)|要比對的指標類型。|
|[reference](#reference)|對應的參考類型。|
|[regex_type](#regex_type)|要比對的規則運算式類型。|
|[value_type](#value_type)|相符項目的類型。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](#op_neq)|比較迭代器是否不相等。|
|[operator*](#op_star)|存取指定的相符項目。|
|[operator++](#op_add_add)|遞增迭代器。|
|[operator=](#op_eq)|比較迭代器是否相等。|
|[operator->](#op_arrow)|存取指定的相符項目。|

## <a name="requirements"></a>需求

**標頭︰**\<regex>

**命名空間：** std

## <a name="examples"></a>範例

如需規則運算式的相關範例，請參閱下列主題：

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

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

## <a name="difference_type"></a>  regex_iterator::difference_type

迭代器差值的類型。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>備註

此類型是 `std::ptrdiff_t` 的同義字。

## <a name="iterator_category"></a>  regex_iterator::iterator_category

迭代器分類的類型。

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>備註

此類型是 `std::forward_iterator_tag` 的同義字。

## <a name="op_neq"></a>  regex_iterator::operator!=

比較迭代器是否不相等。

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的迭代器。

### <a name="remarks"></a>備註

成員函式會傳回 `!(*this == right)`。

## <a name="op_star"></a>  regex_iterator::operator*

存取指定的相符項目。

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>備註

成員函式會傳回儲存的值 `match`。

## <a name="op_add_add"></a>  regex_iterator::operator++

遞增迭代器。

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>備註

如果目前比對沒有任何字元，第一個運算子會呼叫 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`；否則會前進到儲存值 `begin` ，以指向目前比對之後的第一個字元，再呼叫 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`。 不論是哪種情況，如果搜尋失敗，此運算子便會將物件設定為結束序列 (end-of-sequence) 迭代器。 此運算子會傳回該物件。

第二個運算子會複製物件、遞增物件，然後傳回複本。

## <a name="op_eq"></a>  regex_iterator::operator=

比較迭代器是否相等。

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要比較的迭代器。

### <a name="remarks"></a>備註

如果為 true，則傳回此成員函式`*this`並*右*結束序列迭代器或都不是結束序列迭代器和`begin == right.begin`， `end == right.end`， `pregex == right.pregex`，和`flags == right.flags`。 否則會傳回 false。

## <a name="op_arrow"></a>  regex_iterator::operator-&gt;

存取指定的相符項目。

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>備註

此成員函式會傳回儲存值 `match`的位址。

## <a name="pointer"></a>  regex_iterator::pointer

要比對的指標類型。

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>*`同義，其中 `BidIt` 是範本參數。

## <a name="reference"></a>  regex_iterator::reference

對應的參考類型。

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>&`同義，其中 `BidIt` 是範本參數。

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

建構迭代器。

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>參數

*first*<br/>
要比對的序列開頭。

*最後一個*<br/>
要比對的序列結尾。

*re*<br/>
比對的規則運算式。

*f*<br/>
比對的旗標。

### <a name="remarks"></a>備註

第一個建構函式會建構結束序列 (end-of-sequence) 迭代器。 第二個建構函式會初始化儲存的值`begin`與*第一個*，儲存的值`end`與*最後一個*，則預存值`pregex`與`&re`，和預存值`flags`具有*f*。 然後呼叫 `regex_search(begin, end, match, *pregex, flags)`。 如果搜尋失敗，此運算子便會將物件設定為結束序列迭代器。

## <a name="regex_type"></a>  regex_iterator::regex_type

要比對的規則運算式類型。

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `basic_regex<Elem, RXtraits>`的同義字。

## <a name="value_type"></a>  regex_iterator::value_type

相符項目的類型。

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>備註

此類型與 `match_results<BidIt>`同義，其中 `BidIt` 是範本參數。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 類別](../standard-library/regex-constants-class.md)<br/>
[regex_error 類別](../standard-library/regex-error-class.md)<br/>
[\<regex> 函式](../standard-library/regex-functions.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
