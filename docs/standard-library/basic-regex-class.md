---
title: basic_regex 類別
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 8df9e927c430f3b94f5857bf18f575e79d6b922a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453429"
---
# <a name="basicregex-class"></a>basic_regex 類別

包裝規則運算式。

## <a name="syntax"></a>語法

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>參數

*Elem*\
要符合之項目的類型。

*RXtraits*\
項目的 Traits 類別。

## <a name="remarks"></a>備註

此樣板類別描述保存規則運算式的物件。 這個樣板類別的物件可以傳遞至樣板函式[RegEx_match](../standard-library/regex-functions.md#regex_match)、 [RegEx_search](../standard-library/regex-functions.md#regex_search)和[RegEx_replace](../standard-library/regex-functions.md#regex_replace), 以及適當的文字字串引數, 以搜尋符合正則運算式的文字。 這個樣板類別有兩個特製化, 其中的類型定義[RegEx](../standard-library/regex-typedefs.md#regex)適用于**char**類型的元素, 而[wRegEx](../standard-library/regex-typedefs.md#wregex)則是**wchar_t**類型的專案。

樣板引數*RXtraits*會描述樣板類別支援之正則運算式語法的各種重要屬性。 指定這些規則運算式特性的類別必須具有和 [regex_traits Class](../standard-library/regex-traits-class.md) 樣板類別物件相同的外部介面。

有些函式會接受定義規則運算式的運算元序列。 您可以透過數種方法指定這類運算元序列：

`ptr`--以 null 終止的序列 (例如 C 字串, 適用于類型為**char** `ptr`的*Elem* ), 其開頭為 (不能是 null 指標), 其中終止專案是值`value_type()` , 而且不是運算元序列的一部分。

`ptr`, `count` -- `count` 項目序列，開始位置在 `ptr` (這不可以是 null 指標)

`str` -- `basic_string` 物件 `str` 所指定的序列

`first`, `last` -- 由範圍 `first` 中的迭代器 `last` 與 `[first, last)` 分隔的項目序列

`right` -- `basic_regex` 物件 `right`

這些成員函式也會接受`flags`一個引數, 它會指定不同的方法來解讀正則運算式, 以及*RXtraits*類型所描述的選項。

### <a name="members"></a>成員

|成員|預設值|
|-|-|
|public static const flag_type icase|regex_constants::icase|
|public static const flag_type nosubs|regex_constants::nosubs|
|public static const flag_type optimize|regex_constants::optimize|
|public static const flag_type collate|regex_constants::collate|
|public static const flag_type ECMAScript|regex_constants::ECMAScript|
|public static const flag_type basic|regex_constants::basic|
|public static const flag_type extended|regex_constants::extended|
|public static const flag_type awk|regex_constants::awk|
|public static const flag_type grep|regex_constants::grep|
|public static const flag_type egrep|regex_constants::egrep|
|私用 RXtraits 特性||

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[basic_regex](#basic_regex)|建構規則運算式物件|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[flag_type](#flag_type)|語法選項旗標類型。|
|[locale_type](#locale_type)|儲存的地區設定物件類型。|
|[value_type](#value_type)|元素類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[assign](#assign)|將值指派給規則運算式物件。|
|[flags](#flags)|傳回語法選項旗標。|
|[getloc](#getloc)|傳回儲存的地區設定物件。|
|[imbue](#imbue)|修改儲存的地區設定物件。|
|[mark_count](#mark_count)|傳回符合的子運算式數目。|
|[swap](#swap)|交換兩個規則運算式物件。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator=](#op_eq)|將值指派給規則運算式物件。|

## <a name="requirements"></a>需求

**標頭︰** \<regex>

**命名空間：** std

## <a name="example"></a>範例

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="assign"></a>  basic_regex::assign

將值指派給規則運算式物件。

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>參數

*STtraits*\
字串來源的 Traits 類別。

*STalloc*\
字串來源的 Allocator 類別。

*初始*\
輸入範圍來源的迭代器類型。

*再*\
要複製的 Regex 來源。

*指標*\
要複製之序列開頭的指標。

*旗幟*\
要在複製時加入的語法選項旗標。

*len/TD >* \
要複製之序列的長度。

*str*\
要複製的字串。

*頭*\
要複製之序列的開頭。

*次*\
要複製之序列的結尾。

*IList*\
要複製的 initializer_list。

### <a name="remarks"></a>備註

成員函式會分別將 `*this` 所含的規則運算式取代為運算元序列所描述的規則運算式，然後傳回 `*this`。

## <a name="basic_regex"></a>  basic_regex::basic_regex

建構規則運算式物件

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>參數

*STtraits*\
字串來源的 Traits 類別。

*STalloc*\
字串來源的 Allocator 類別。

*初始*\
輸入範圍來源的迭代器類型。

*再*\
要複製的 Regex 來源。

*指標*\
要複製之序列開頭的指標。

*旗幟*\
要在複製時加入的語法選項旗標。

*len/TD >* \
要複製之序列的長度。

*str*\
要複製的字串。

*頭*\
要複製之序列的開頭。

*次*\
要複製之序列的結尾。

*IList*\
要複製的 initializer_list。

### <a name="remarks"></a>備註

所有的建構函式都會儲存 `RXtraits` 類型的預設建構物件。

第一個建構函式會建構空的 `basic_regex` 物件。 其他建構函式會建構 `basic_regex` 物件，其保存運算元序列所描述的規則運算式。

當傳遞`basic_regex`給[RegEx_match](../standard-library/regex-functions.md#regex_match)、 [RegEx_search](../standard-library/regex-functions.md#regex_search)或[RegEx_replace](../standard-library/regex-functions.md#regex_replace)時, 空的物件不符合任何字元序列。

## <a name="flag_type"></a>  basic_regex::flag_type

語法選項旗標類型。

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>備註

此類型與 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 同義。

## <a name="flags"></a>  basic_regex::flags

傳回語法選項旗標。

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回 `flag_type` 引數的值，再將該值傳遞至 [basic_regex::assign](#assign) 成員函式之一的最新呼叫；如果沒有這類呼叫，則會將該值傳遞至建構函式。

## <a name="getloc"></a>  basic_regex::getloc

傳回儲存的地區設定物件。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>備註

此成員函式會傳回 `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`。

## <a name="imbue"></a>  basic_regex::imbue

修改儲存的地區設定物件。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>參數

*loc*\
要儲存的地區設定物件。

### <a name="remarks"></a>備註

此成員函式會清空 `*this` 並傳回 `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`。

## <a name="locale_type"></a>  basic_regex::locale_type

儲存的地區設定物件類型。

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>備註

此類型與 [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type) 同義。

## <a name="mark_count"></a>  basic_regex::mark_count

傳回符合的子運算式數目。

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>備註

成員函式會傳回規則運算式中的擷取群組數目。

## <a name="op_eq"></a>  basic_regex::operator=

將值指派給規則運算式物件。

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>參數

*STtraits*\
字串來源的 Traits 類別。

*STalloc*\
字串來源的 Allocator 類別。

*再*\
要複製的 Regex 來源。

*str*\
要複製的字串。

### <a name="remarks"></a>備註

這些運算子會分別將 `*this` 所含的規則運算式取代為運算元序列所描述的規則運算式，然後傳回 `*this`。

## <a name="swap"></a>  basic_regex::swap

交換兩個規則運算式物件。

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>參數

*再*\
要交換的規則運算式物件。

### <a name="remarks"></a>備註

此成員函式會在和`*this` *right*之間交換正則運算式。 它會在固定時間執行但不會擲回任何例外狀況。

## <a name="value_type"></a>  basic_regex::value_type

元素類型。

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>備註

此類型與範本參數*Elem*同義。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits 類別](../standard-library/regex-traits-class.md)
