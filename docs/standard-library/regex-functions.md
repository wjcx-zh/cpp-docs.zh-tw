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
ms.openlocfilehash: ff6ea37208aef19431bf7aefe612dccd589c638b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374536"
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt; 函式

|||
|-|-|
|[regex_match](#regex_match)|測試規則運算式是否符合整個目標字串。|
|[regex_replace](#regex_replace)|取代符合的規則運算式。|
|[regex_search](#regex_search)|搜尋規則運算式相符項目。|
|[交換](#swap)|交換兩`basic_regex`個或`match_results`物件。|

## <a name="regex_match"></a><a name="regex_match"></a>regex_match

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

*比比*\
子相符項目的迭代器類型。 對於常見情況,此為`string::const_iterator``wstring::const_iterator`或`const char*``const wchar_t*`。

*Alloc*\
符合結果配置器類別。

*埃萊姆*\
要符合之項目的類型。 對於常見情況,這是`string``wstring` `char*` `wchar_t*`, 或 。

*RXtraits*\
項目的 Traits 類別。

*Alloc2*\
規則運算式配置器類別。

*IOtraits*\
字串特性類別。

*伊奧洛克*\
字串配置器類別。

*標誌*\
比對的旗標。

*第一*\
要比對的序列開頭。

*最後*\
要比對的序列結尾。

*符合*\
比對結果。 對應於 Elem[smatch](../standard-library/regex-typedefs.md#smatch)類型`string`:的匹配,[的](../standard-library/regex-typedefs.md#wsmatch)`wstring`匹配,`char*``wchar_t*`的匹配,cmatch 的 或[的 wcmatch。](../standard-library/regex-typedefs.md#wcmatch) [cmatch](../standard-library/regex-typedefs.md#cmatch)

*Ptr*\
要比對之序列開頭的指標。 如果*ptr*是`char*``cmatch`,`regex`則使用與 。 使用*ptr,*`wchar_t*``wcmatch``wregex`則使用與 。

*re*\
要比對的規則運算式。 鍵入`regex``string`與`char*`或`wregex``wstring` `wchar_t*` 。

*Str*\
要比對的字串。 對應於*Elem*的類型。

### <a name="remarks"></a>備註

僅當整個操作符序列*str*與正則運算式參數*re*完全匹配時,每個樣本函數才返回 true。 使用[regex_search](../standard-library/regex-functions.md#regex_search)符合目標序列中的子字串`regex_iterator`並 尋找多個匹配項。 使用 `match_results` 物件的函式會設定其成員，以反映比對是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

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

## <a name="regex_replace"></a><a name="regex_replace"></a>regex_replace

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

*出它*\
適用於取代項目的迭代器類型。

*比比*\
子相符項目的迭代器類型。

*RXtraits*\
項目的 Traits 類別。

*Alloc*\
規則運算式配置器類別。

*埃萊姆*\
要符合之項目的類型。

*標誌*\
比對的旗標。

*第一*\
要比對的序列開頭。

*Fmt*\
取代項目的格式。

*最後*\
要比對的序列結尾。

*出*\
輸出迭代器。

*re*\
要比對的規則運算式。

*Str*\
要比對的字串。

### <a name="remarks"></a>備註

第一個函數構造[regex_iterator類](../standard-library/regex-iterator-class.md)`iter(first, last, re, flags)`物件,並用它來`[first, last)`將其輸入 範圍拆分為一`T0 M0 T1 M1...TN-1 MN-1 TN`系列子`Mn`序列 ,其中 反覆運算器檢測到的第 n 個匹配項。 如果找不到相符項，`T0` 是整個輸入範圍且 `N` 為零。 如果 `(flags & format_first_only) != 0`，就只會使用第一個相符項、`T1` 是緊接在相符項之後的所有輸入文字，而 `N` 為 1。 對於範圍內`i``[0, N)`的每個 ,`(flags & format_no_copy) == 0`如果將`Ti`範圍內的文字複製到反覆運算器*出*。`m.format(out, fmt, flags)`然後調用 ,`m`其中`match_results`是`iter``Mi`子 序列的反覆運算器物件返回的物件。 最後,如果它`(flags & format_no_copy) == 0`將`TN`範圍內的文字複製到反覆運算器*出*。函數傳回 *。*

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

## <a name="regex_search"></a><a name="regex_search"></a>regex_search

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

*比比*\
子相符項目的迭代器類型。

*Alloc*\
符合結果配置器類別。

*埃萊姆*\
要符合之項目的類型。

*RXtraits*\
項目的 Traits 類別。

*Alloc2*\
規則運算式配置器類別。

*IOtraits*\
字串特性類別。

*伊奧洛克*\
字串配置器類別。

*標誌*\
比對的旗標。

*第一*\
要比對的序列開頭。

*最後*\
要比對的序列結尾。

*符合*\
比對結果。

*Ptr*\
要比對之序列開頭的指標。

*re*\
要比對的規則運算式。

*Str*\
要比對的字串。

### <a name="remarks"></a>備註

僅當搜索其正則表達式參數*在其*操作順序中成功時,每個範本函數才返回 true。 使用 `match_results` 物件的函式會設定其成員，以反映搜尋是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

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

## <a name="swap"></a><a name="swap"></a>交換

交換兩`basic_regex`個或`match_results`物件。

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

*埃萊姆*\
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

[\<正則>](../standard-library/regex.md)\
[regex_constants類](../standard-library/regex-constants-class.md)\
[regex_error類](../standard-library/regex-error-class.md)\
[regex_iterator類](../standard-library/regex-iterator-class.md)\
[\<正則>運算子](../standard-library/regex-operators.md)\
[regex_token_iterator類](../standard-library/regex-token-iterator-class.md)\
[regex_traits類](../standard-library/regex-traits-class.md)\
[\<正則>型態](../standard-library/regex-typedefs.md)
