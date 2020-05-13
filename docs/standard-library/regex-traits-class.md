---
title: regex_traits 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 8879336c48d0fec8a20411abf1c07d570a1575e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366385"
---
# <a name="regex_traits-class"></a>regex_traits 類別

描述進行比對的元素特性。

## <a name="syntax"></a>語法

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>參數

*埃萊姆*\
要描述的字元項目類型。

## <a name="remarks"></a>備註

類範本描述*Elem*類型的各種正則運算式特徵。 [類basic_regex類](../standard-library/basic-regex-class.md)使用此資訊來操作*Elem*類型的元素。

每個 `regex_traits` 物件都擁有一個類型 `regex_traits::locale` 的物件，這種類型可為其部分成員函式使用。 預設的地區設定是 `regex_traits::locale()`的複本。 成員函式 `imbue` 取代了地區設定物件，而成員函式 `getloc` 會傳回地區設定物件的複本。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[regex_traits](#regex_traits)|建構物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_class_type](#char_class_type)|字元類別指示項的類型。|
|[char_type](#char_type)|項目的類型。|
|[locale_type](#locale_type)|儲存的地區設定物件類型。|
|[size_type](#size_type)|序列長度的類型。|
|[string_type](#string_type)|元素字串的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[貝洛克](#getloc)|傳回儲存的地區設定物件。|
|[imbue](#imbue)|修改儲存的地區設定物件。|
|[是型](#isctype)|測試是否有類別成員資格。|
|[長度](#length)|傳回 null 中止序列的長度。|
|[lookup_classname](#lookup_classname)|將序列對應至字元類別。|
|[lookup_collatename](#lookup_collatename)|將序列對應至定序項目。|
|[變換](#transform)|轉換成相等的已排序序列。|
|[transform_primary](#transform_primary)|轉換成相等且不區分大小寫的已排序序列。|
|[翻譯](#translate)|轉換成相等的相符元素。|
|[translate_nocase](#translate_nocase)|轉換成相等且不區分大小寫的相符項目。|
|[值](#value)|將項目轉換成數值。|

## <a name="requirements"></a>需求

**標頭︰** \<regex>

**命名空間：** std

## <a name="example"></a>範例

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="regex_traitschar_class_type"></a><a name="char_class_type"></a>regex_traits:char_class_type

字元類別指示項的類型。

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>備註

此類型是指定字元類別之未指定類型的同義字。 這個類型的值可以透過 `|` 運算子來結合，以指定做為運算元所指定之類別聯集的字元類別。

## <a name="regex_traitschar_type"></a><a name="char_type"></a>regex_traits:char_type

項目的類型。

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>備註

typedef 是範本引數 `Elem`的同義字。

## <a name="regex_traitsgetloc"></a><a name="getloc"></a>regex_traits:getloc

傳回儲存的地區設定物件。

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>備註

成員函式會傳回儲存的 `locale` 物件。

## <a name="regex_traitsimbue"></a><a name="imbue"></a>regex_traits::英布埃

修改儲存的地區設定物件。

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>參數

*loc*\
要儲存的地區設定物件。

### <a name="remarks"></a>備註

成員函數將*loc*複製到儲存`locale`的物件,並返回儲存`locale`物件的上一個值的副本。

## <a name="regex_traitsisctype"></a><a name="isctype"></a>regex_traits:isc型

測試是否有類別成員資格。

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>參數

*ch*\
待測試的項目。

*Cls*\
做為測試對象的類別。

### <a name="remarks"></a>備註

僅當字元*ch*位於*cls*指定的字元類中時,成員函數才返回 true。

## <a name="regex_traitslength"></a><a name="length"></a>regex_traits:長度

傳回 null 中止序列的長度。

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>參數

*Str*\
null 終止序列。

### <a name="remarks"></a>備註

此靜態成員函式傳回 `std::char_traits<char_type>::length(str)`。

## <a name="regex_traitslocale_type"></a><a name="locale_type"></a>regex_traits:locale_type

儲存的地區設定物件類型。

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>備註

Typedef 是封裝地區設定之類型的同義字。 在特製化 `regex_traits<char>` 和 `regex_traits<wchar_t>` 時，此為 `std::locale`的同義字。

## <a name="regex_traitslookup_classname"></a><a name="lookup_classname"></a>regex_traits:lookup_classname

將序列對應至字元類別。

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>參數

*第一*\
要查閱之序列的開頭。

*最後*\
要查閱之序列的結尾。

### <a name="remarks"></a>備註

成員函式會傳回一個值，指定由字元序列命名、依引數指向的字元類別。 此值不依存於序列中字元的大小寫。

特製化 `regex_traits<char>` 會辨識名稱 `"d"`、`"s"`、`"w"`、`"alnum"`、`"alpha"`、`"blank"`、`"cntrl"`、`"digit"`、`"graph"`、`"lower"`、`"print"`、`"punct"`、`"space"`、`"upper"` 和 `"xdigit"`，且完全不考量大小寫。

特製化 `regex_traits<wchar_t>` 會辨識名稱 `L"d"`、`L"s"`、`L"w"`、`L"alnum"`、`L"alpha"`、`L"blank"`、`L"cntrl"`、`L"digit"`、`L"graph"`、`L"lower"`、`L"print"`、`L"punct"`、`L"space"`、`L"upper"` 和 `L"xdigit"`，且完全不考量大小寫。

## <a name="regex_traitslookup_collatename"></a><a name="lookup_collatename"></a>regex_traits:lookup_collatename

將序列對應至定序項目。

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>參數

*第一*\
要查閱之序列的開頭。

*最後*\
要查閱之序列的結尾。

### <a name="remarks"></a>備註

此成員函式會傳回含有對應至序列 `[first, last)`之定序項目的字串物件；如果序列不是有效的定序項目，則傳回空字串。

## <a name="regex_traitsregex_traits"></a><a name="regex_traits"></a>regex_traits:regex_traits

建構物件。

```cpp
regex_traits();
```

### <a name="remarks"></a>備註

建構函式會建構已儲存的 `locale` 物件初始化為預設地區設定的物件。

## <a name="regex_traitssize_type"></a><a name="size_type"></a>regex_traits:size_type

序列長度的類型。

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>備註

此 typedef 是不帶正負號之整數類型的同義字。 在特製化 `regex_traits<char>` 和 `regex_traits<wchar_t>` 時，此為 `std::size_t`的同義字。

此 typedef 是 `std::size_t`的同義字。

## <a name="regex_traitsstring_type"></a><a name="string_type"></a>regex_traits:string_type

元素字串的類型。

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>備註

此 typedef 是 `basic_string<Elem>`的同義字。

## <a name="regex_traitstransform"></a><a name="transform"></a>regex_traits:轉換

轉換成相等的已排序序列。

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>參數

*第一*\
要轉換之序列的開頭。

*最後*\
要轉換之序列的結尾。

### <a name="remarks"></a>備註

此成員函式會傳回根據儲存的 `locale` 物件，使用轉換規則所產生的字串。 至於迭代器範圍 `[first1, last1)` 和 `[first2, last2)`所指定的兩個字元序列，如果迭代器範圍 `transform(first1, last1) < transform(first2, last2)` 所指定的字元序列排在迭代器範圍 `[first1, last1)` 所指定的字元序列前面，則 `[first2, last2)`。

## <a name="regex_traitstransform_primary"></a><a name="transform_primary"></a>regex_traits:transform_primary

轉換成相等且不區分大小寫的已排序序列。

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>參數

*第一*\
要轉換之序列的開頭。

*最後*\
要轉換之序列的結尾。

### <a name="remarks"></a>備註

此成員函式會傳回根據儲存的 `locale` 物件，使用轉換規則所產生的字串。 至於迭代器範圍 `[first1, last1)` 和 `[first2, last2)`所指定的兩個字元序列，如果迭代器範圍 `transform_primary(first1, last1) < transform_primary(first2, last2)` 所指定的字元序列排在迭代器範圍 `[first1, last1)` 所指定的字元序列前面，則 `[first2, last2)` ，而不必考慮大小寫或腔調字。

## <a name="regex_traitstranslate"></a><a name="translate"></a>regex_traits:翻譯

轉換成相等的相符元素。

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換的元素。

### <a name="remarks"></a>備註

使用取決於預存 `locale` 物件的轉換規則，成員函式會傳回它產生的字元。 至於兩個 `char_type` 物件 `ch1` 和 `ch2`，唯有 `translate(ch1) == translate(ch2)` 和 `ch1` 符合這個情況：一個發生在規則運算式定義，另一個發生在區分地區設定相符項目之目標序列的對應位置時，才會是 `ch2` 。

## <a name="regex_traitstranslate_nocase"></a><a name="translate_nocase"></a>regex_traits:translate_nocase

轉換成相等且不區分大小寫的相符項目。

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換的元素。

### <a name="remarks"></a>備註

使用取決於預存 `locale` 物件的轉換規則，成員函式會傳回它產生的字元。 至於兩個 `char_type` 物件 `ch1` 和 `ch2`，唯有 `translate_nocase(ch1) == translate_nocase(ch2)` 和 `ch1` 符合這個情況：一個發生在規則運算式定義，另一個發生在區分大小寫相符項目之目標序列的對應位置時，才會是 `ch2` 。

## <a name="regex_traitsvalue"></a><a name="value"></a>regex_traits:值

將項目轉換成數值。

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換的元素。

*拉迪克斯*\
要使用的算術基底。

### <a name="remarks"></a>備註

成員函數返回由基*半徑*中的字元*ch*表示的值,如果*ch*不是基*半徑*中的有效數位,則返回 -1。 函數將僅使用*半徑*參數 8、10 或 16 調用。

## <a name="see-also"></a>另請參閱

[\<正則>](../standard-library/regex.md)\
[regex_constants類](../standard-library/regex-constants-class.md)\
[regex_error類](../standard-library/regex-error-class.md)\
[\<正規表示式>函數](../standard-library/regex-functions.md)\
[regex_iterator類](../standard-library/regex-iterator-class.md)\
[\<正則>運算子](../standard-library/regex-operators.md)\
[regex_token_iterator類](../standard-library/regex-token-iterator-class.md)\
[\<正則>型態](../standard-library/regex-typedefs.md)\
[regex_traits\<字元>類](../standard-library/regex-traits-char-class.md)\
[regex_traits\<wchar_t> 類別](../standard-library/regex-traits-wchar-t-class.md)
