---
title: '&lt;regex&gt; 函式'
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: b2be3e4a830113ee86a05fea0d39fd8e12ec3e9a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451582"
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt; 函式

|||
|-|-|
|[regex_match](#regex_match)|測試規則運算式是否符合整個目標字串。|
|[regex_replace](#regex_replace)|取代符合的規則運算式。|
|[regex_search](#regex_search)|搜尋規則運算式相符項目。|
|[swap](#swap)|交換兩`basic_regex`個`match_results`或物件。|

## <a name="regex_match"></a>  regex_match

測試規則運算式是否符合整個目標字串。

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>參數

*BidIt*\
子相符項目的迭代器類型。 `string::const_iterator`在一般情況下`wstring::const_iterator` `const wchar_t*`, 這其中一個、或。`const char*`

*配置*\
符合結果配置器類別。

*Elem*\
要符合之項目的類型。 `string`在一般情況下`wstring` `wchar_t*`, 這是、或。`char*`

*RXtraits*\
項目的 Traits 類別。

*Alloc2*\
規則運算式配置器類別。

*IOtraits*\
字串特性類別。

*IOalloc*\
字串配置器類別。

*旗幟*\
比對的旗標。

*頭*\
要比對的序列開頭。

*次*\
要比對的序列結尾。

*使*\
比對結果。 對應至 Elem 類型: [](../standard-library/regex-typedefs.md#smatch)適用于`string`的 smatch、 `wstring`適用于的`char*` [wsmatch (](../standard-library/regex-typedefs.md#wsmatch) 、 [cmatch](../standard-library/regex-typedefs.md#cmatch)或[wcmatch](../standard-library/regex-typedefs.md#wcmatch) `wchar_t*`。

*指標*\
要比對之序列開頭的指標。 如果*ptr*為`char*`, 請使用`cmatch`和`regex`。 如果*ptr* , `wchar_t*`則會`wcmatch`使用`wregex`和。

*重新*\
要比對的規則運算式。 針對`regex` `wregex`和, 請輸入,或針對`wstring`和。`wchar_t*` `string` `char*`

*str*\
要比對的字串。 對應至*Elem*的類型。

### <a name="remarks"></a>備註

只有當整個運算元序列*str*完全符合正則運算式引數時, 每個範本函數才會傳回 true。 使用[RegEx_search](../standard-library/regex-functions.md#regex_search)來比對目標序列內的子字串`regex_iterator` , 並尋找多個相符專案。 使用 `match_results` 物件的函式會設定其成員，以反映比對是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

使用 `match_results` 物件的函式會設定其成員，以反映比對是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

### <a name="example"></a>範例

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a>  regex_replace

取代符合的規則運算式。

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>參數

*OutIt*\
適用於取代項目的迭代器類型。

*BidIt*\
子相符項目的迭代器類型。

*RXtraits*\
項目的 Traits 類別。

*配置*\
規則運算式配置器類別。

*Elem*\
要符合之項目的類型。

*旗幟*\
比對的旗標。

*頭*\
要比對的序列開頭。

*bcp.fmt*\
取代項目的格式。

*次*\
要比對的序列結尾。

*out*\
輸出迭代器。

*重新*\
要比對的規則運算式。

*str*\
要比對的字串。

### <a name="remarks"></a>備註

第一個函式會建立[RegEx_iterator 類別](../standard-library/regex-iterator-class.md)物件`iter(first, last, re, flags)` , 並使用它將其輸入`[first, last)`範圍分割成一系列`T0 M0 T1 M1...TN-1 MN-1 TN`的個子序列`Mn` , 其中是反覆運算器偵測到的第 n 個相符項。 如果找不到相符項，`T0` 是整個輸入範圍且 `N` 為零。 如果 `(flags & format_first_only) != 0`，就只會使用第一個相符項、`T1` 是緊接在相符項之後的所有輸入文字，而 `N` 為 1。 針對範圍`i` `(flags & format_no_copy) == 0` `Ti` 中的每個, 如果它將範圍中的文字複製到反覆運算器輸出。 `[0, N)`然後呼叫 `m.format(out, fmt, flags)`，其中 `m` 是子序列 `Mi` 的 `iter` 迭代器物件所傳回的 `match_results` 物件。 最後, 如果`(flags & format_no_copy) == 0`將範圍`TN`中的文字複製到反覆運算器, 則為。函數會傳回*out*。

第二個函式會建構 `basic_string<charT>` 類型的區域變數 `result`，並呼叫 `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`。 它會傳回 `result`。

### <a name="example"></a>範例

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a>  regex_search

搜尋規則運算式相符項目。

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>參數

*BidIt*\
子相符項目的迭代器類型。

*配置*\
符合結果配置器類別。

*Elem*\
要符合之項目的類型。

*RXtraits*\
項目的 Traits 類別。

*Alloc2*\
規則運算式配置器類別。

*IOtraits*\
字串特性類別。

*IOalloc*\
字串配置器類別。

*旗幟*\
比對的旗標。

*頭*\
要比對的序列開頭。

*次*\
要比對的序列結尾。

*使*\
比對結果。

*指標*\
要比對之序列開頭的指標。

*重新*\
要比對的規則運算式。

*str*\
要比對的字串。

### <a name="remarks"></a>備註

只有在搜尋其正則運算式引數的運算元順序成功時 , 每個範本函式才會傳回 true。 使用 `match_results` 物件的函式會設定其成員，以反映搜尋是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

### <a name="example"></a>範例

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a>  swap

交換兩`basic_regex`個`match_results`或物件。

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>參數

*Elem*\
要符合之項目的類型。

*RXtraits*\
項目的 Traits 類別。

### <a name="remarks"></a>備註

範本函式會在固定時間交換其各自引數的內容，且不會擲回例外狀況。

### <a name="example"></a>範例

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[RegEx_constants 類別](../standard-library/regex-constants-class.md)\
[RegEx_error 類別](../standard-library/regex-error-class.md)\
[RegEx_iterator 類別](../standard-library/regex-iterator-class.md)\
[\<RegEx > 運算子](../standard-library/regex-operators.md)\
[RegEx_token_iterator 類別](../standard-library/regex-token-iterator-class.md)\
[RegEx_traits 類別](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
