---
title: match_results 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 8ce9ed987baf63f2cc9f095e2955a8165e977193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212211"
---
# <a name="match_results-class"></a>match_results 類別

保留子相符項目的序列。

## <a name="syntax"></a>語法

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>參數

*BidIt*\
子相符項目的迭代器類型。

*配置*\
管理儲存體的配置器類型。

## <a name="remarks"></a>備註

類別樣板描述的物件可控制 `sub_match<BidIt>` 正則運算式搜尋所產生之類型專案的不可修改序列。 每個項目會指向符合對應至該項目之擷取群組的子序列。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[match_results](#match_results)|建構物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[allocator_type](#allocator_type)|管理儲存體的配置器類型。|
|[char_type](#char_type)|項目的類型。|
|[const_iterator](#const_iterator)|子相符項目的 const 迭代器類型。|
|[const_reference](#const_reference)|元素 const 參考的類型。|
|[difference_type](#difference_type)|迭代器差值的類型。|
|[定位](#iterator)|子相符項目的迭代器類型。|
|[reference](#reference)|元素參考的類型。|
|[size_type](#size_type)|子相符項目計數的類型。|
|[string_type](#string_type)|字串的類型。|
|[value_type](#value_type)|子對應的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[起點](#begin)|指定子相符項目序列的開頭。|
|[empty](#empty)|測試是否沒有任何子相符項目。|
|[成品](#end)|指定子相符項目序列的結尾。|
|[format](#format)|格式子相符項目。|
|[get_allocator](#get_allocator)|傳回已儲存的配置器。|
|[length](#length)|傳回子相符項目的長度。|
|[max_size](#max_size)|取得最大子相符項目數。|
|[移動](#position)|取得子群組的起始位移。|
|[prefix](#prefix)|取得第一個子相符項目之前的序列。|
|[size](#size)|計算子相符項目數。|
|[字串](#str)|傳回子相符項目。|
|[尾碼](#suffix)|取得最後一個子相符項目之後的序列。|
|[調換](#swap)|交換兩個 match_results 物件。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator =](#op_eq)|複製 match_results 物件。|
|[操作\[\]](#op_at)|存取子物件。|

## <a name="requirements"></a>需求

**標頭：**\<regex>

**命名空間：** std

## <a name="example"></a>範例

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results：： allocator_type

管理儲存體的配置器類型。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>備註

Typedef 是*範本引數*配置的同義字。

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results：： begin

指定子相符項目序列的開頭。

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>備註

成員函式傳回的隨機存取迭代器，指向序列的第一個項目 (或空序列結尾以外的位置)。

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results：： char_type

項目的類型。

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>備註

這個 typedef 與 `iterator_traits<BidIt>::value_type`類型同義，後者是搜尋到之字元序列的項目類型。

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results：： const_iterator

子相符項目的 const 迭代器類型。

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>備註

此 typedef 所描述的物件可做為受控制序列的常數隨機存取迭代器。

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results：： const_reference

元素 const 參考的類型。

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>備註

typedef 所說明的物件可作為受控制序列之元素的常數參考。

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results：:d ifference_type

迭代器差值的類型。

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>備註

Typedef 是 `iterator_traits<BidIt>::difference_type`類型的同義字；它描述一個物件，可以代表指向受控制序列中項目之任何兩個迭代器間的差值。

## <a name="match_resultsempty"></a><a name="empty"></a>match_results：： empty

測試是否沒有任何子相符項目。

```cpp
bool empty() const;
```

### <a name="remarks"></a>備註

只有在規則運算式搜尋失敗時，此成員函式才會傳回 true。

## <a name="match_resultsend"></a><a name="end"></a>match_results：： end

指定子相符項目序列的結尾。

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>備註

成員函式會傳回指向序列結尾之外的迭代器。

## <a name="match_resultsformat"></a><a name="format"></a>match_results：： format

格式子相符項目。

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>參數

*OutIt*\
輸出迭代器類型。

*脫銷*\
要寫入的輸出資料流。

*bcp.fmt*\
格式字串。

*旗幟*\
格式旗標。

### <a name="remarks"></a>備註

每個成員函式都會在*bcp.fmt*格式的控制項底下產生格式化的文字。 第一個成員函式會將格式化的文字寫入*其引數*所定義的序列，並傳回*out*。第二個成員函式會傳回字串物件，其中包含格式化文字的複本。

若要產生格式化文字， 格式字串中的常值文字通常會複製到目標序列。 格式字串中的每個逸出序列由所代表的文字取代。 複製和取代的詳細資料受到傳遞至函式的格式旗標控制。

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results：： get_allocator

傳回已儲存的配置器。

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回所使用的配置器物件複本 **`*this`** ，以配置其 `sub_match` 物件。

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results：： iterator

子相符項目的迭代器類型。

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>備註

此類型說明可作為受控制序列之隨機存取迭代器的物件。

## <a name="match_resultslength"></a><a name="length"></a>match_results：： length

傳回子相符項目的長度。

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>參數

*sub*\
子相符項目的索引。

### <a name="remarks"></a>備註

成員函式會傳回 `(*this)[sub].length()`。

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results：： match_results

建構物件。

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>參數

*配置*\
要儲存的配置器物件。

*再*\
要複製的 match_results 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構不含子相符項目的 `match_results` 物件。 第二個函式 `match_results` 會建立屬於*right*複本的物件。

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results：： max_size

取得最大子相符項目數。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>備註

成員函式會傳回物件可以控制的最長序列的長度。

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results：： operator =

複製 match_results 物件。

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>參數

*再*\
要複製的 match_results 物件。

### <a name="remarks"></a>備註

成員運算子會將所控制的序列取代為 **`*this`** *right*所控制的序列複本。

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results：： operator []

存取子物件。

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>參數

*位*\
子相符項目的索引。

### <a name="remarks"></a>備註

此成員函式會傳回受控制序列之元素*n*的參考，或 `sub_match` 如果 `size() <= n` capture 群組*n*不是相符專案的一部分，則傳回空物件的參考。

## <a name="match_resultsposition"></a><a name="position"></a>match_results：:p o

取得子群組的起始位移。

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>參數

*sub*\
子相符項目的索引。

### <a name="remarks"></a>備註

此成員函式會傳回 `std::distance(prefix().first, (*this)[sub].first)`，也就是從目標序列中的第一個字元，到受控制序列的 `n` 項目所指向的子相符項目中第一個字元之間的距離。

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results：:p refix

取得第一個子相符項目之前的序列。

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回 `sub_match<BidIt>` 類型物件的參考，以指向起始於目標序列開頭並結束於 `(*this)[0].first`的字元序列，也就是指向相符子序列之前的文字。

## <a name="match_resultsreference"></a><a name="reference"></a>match_results：： reference

元素參考的類型。

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>備註

這個類型與類型 `const_reference`同義。

## <a name="match_resultssize"></a><a name="size"></a>match_results：： size

計算子相符項目數。

```cpp
size_type size() const;
```

### <a name="remarks"></a>備註

如果用於搜尋的數目超過規則運算式中的擷取群組數目，此成員函式會傳回 1；如果不進行搜尋，則會傳回 0。

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results：： size_type

子相符項目計數的類型。

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>備註

這個類型與類型 `Alloc::size_type`同義。

## <a name="match_resultsstr"></a><a name="str"></a>match_results：： str

傳回子相符項目。

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>參數

*sub*\
子相符項目的索引。

### <a name="remarks"></a>備註

成員函式會傳回 `string_type((*this)[sub])`。

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results：： string_type

字串的類型。

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>備註

這個類型與類型 `basic_string<char_type>`同義。

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results：：尾碼

取得最後一個子相符項目之後的序列。

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回 `sub_match<BidIt>` 類型物件的參考，以指向起始於 `(*this)[size() - 1].second` 並結束於目標序列結尾的字元序列，也就是指向相符子序列之後的文字。

## <a name="match_resultsswap"></a><a name="swap"></a>match_results：： swap

交換兩個 match_results 物件。

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>參數

*再*\
要交換的 match_results 物件。

### <a name="remarks"></a>備註

成員函式 **`*this`** 會以常數時間交換和的內容，*而不*會擲回例外狀況。

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results：： value_type

子對應的類型。

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>備註

typedef 與類型 `sub_match<BidIt>`同義。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)
