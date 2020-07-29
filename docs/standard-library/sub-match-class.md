---
title: sub_match 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 57aa4ec366588f71f41a747a2dc5127f87ea2e2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222195"
---
# <a name="sub_match-class"></a>sub_match 類別

描述子相符項目。

## <a name="syntax"></a>語法

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>參數

*BidIt*\
子相符項目的迭代器類型。

## <a name="remarks"></a>備註

類別樣板描述一個物件，它會指定一系列的字元，以便在[RegEx_match](../standard-library/regex-functions.md#regex_match)或[RegEx_search](../standard-library/regex-functions.md#regex_search)的呼叫中符合捕捉群組。 類型為 [match_results 類別](../standard-library/match-results-class.md)的物件會保存這些物件的陣列，每個陣列分別代表用於搜尋之規則運算式中的一個擷取群組。

如果擷取群組與物件的資料成員不符，則 `matched` 為 false，且兩個迭代器 `first` 和 `second` (繼承自基底 `std::pair`) 相等。 如果擷取群組相符，則 `matched` 為 true，迭代器 `first` 會指向目標序列中符合擷取群組的第一個字元，而 `second` 會指向目標序列中符合擷取群組之最後一個字元後的一個位置。 請注意，如果零長度與成員相符，則 `matched` 為零，且兩個迭代器相等，並且都會指向相符項目的位置。

當擷取群組只包含一個判斷提示，或包含一個允許重複零的重複項目時，可能會發生零長度相符的情況。 例如：

"^" 與目標序列 "a" 相符；對應至擷取群組 0 的 `sub_match` 物件會保存同時指向序列中第一個字元的兩個迭代器。

"b(a*)b" 與目標序列 "bb" 相符；對應至擷取群組 1 的 `sub_match` 物件會保存同時指向序列中第二個字元的兩個迭代器。

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[difference_type](#difference_type)|迭代器差值的類型。|
|[定位](#iterator)|迭代器的類型。|
|[value_type](#value_type)|項目的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[何](#compare)|比較子相符項目與序列。|
|[length](#length)|傳回子相符項目的長度。|
|[相符](#matched)|指出比對是否成功。|
|[字串](#str)|將子對應轉換成字串。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[運算子 basic_string<value_type>](#op_basic_string_lt_value_type_gt)|將子相符項目轉換成字串。|

## <a name="example"></a>範例

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>需求

**標頭：**\<regex>

**命名空間：** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match：： compare

比較子相符項目與序列。

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>參數

*再*\
要比較子相符項目。

*str*\
要比較的字串。

*指標*\
要比較的以 null 終止的序列。

### <a name="remarks"></a>備註

第一個成員函式會比較比對序列 `[first, second)` 與比對序列 `[right.first, right.second)`。 第二個成員函式會比較比對序列 `[first, second)` 與字元序列 `[right.begin(), right.end())`。 第三個成員函式會比較比對序列 `[first, second)` 與字元序列 `[right, right + std::char_traits<value_type>::length(right))`。

每個函式會傳回：

如果比對序列中的第一個不同的值小於運算元序列中的對應元素 (由 `std::char_traits<value_type>::compare` 決定)，或如果兩者有共同的前置詞、但目標序列較長，則為負值

如果兩者的比較元素相等，且具有相同長度，則為零

否則為正值。

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match：:d ifference_type

迭代器差值的類型。

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `iterator_traits<BidIt>::difference_type`的同義字。

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match：： iterator

迭代器的類型。

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>備註

typedef 是範本類型引數 `Bidit` 的同義字。

## <a name="sub_matchlength"></a><a name="length"></a>sub_match：： length

傳回子相符項目的長度。

```cpp
difference_type length() const;
```

### <a name="remarks"></a>備註

成員函式會傳回相符序列的長度，如果沒有相符序列則傳回零。

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match：：符合

指出比對是否成功。

```cpp
bool matched;
```

### <a name="remarks"></a>備註

**`true`** 只有當與關聯的 capture 群組 **`*this`** 是正則運算式比對的一部分時，成員才會保存。

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match：： operator basic_string &lt; value_type&gt;

將子相符項目轉換成字串。

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>備註

成員運算子會傳回 `str()`。

## <a name="sub_matchstr"></a><a name="str"></a>sub_match：： str

將子對應轉換成字串。

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>備註

成員函式會傳回 `basic_string<value_type>(first, second)`。

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match：： value_type

項目的類型。

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `iterator_traits<BidIt>::value_type`的同義字。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
