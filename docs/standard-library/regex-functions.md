---
title: '&lt;regex&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
dev_langs:
- C++
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: 7c89f5509ec37e1ef91e92acb6732d1b4819f930
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ltregexgt-functions"></a>&lt;regex&gt; 函式

||||
|-|-|-|
|[regex_match](#regex_match)|[regex_replace](#regex_replace)|[regex_search](#regex_search)|
|[swap](#swap)|

## <a name="regex_match"></a>  regex_match

測試規則運算式是否符合整個目標字串。

```

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

`BidIt` 子相符項目的迭代器類型。 在一般情況下，這會是 string::const_iterator、wstring::const_iterator、const char* 或 const wchar_t\*。

`Alloc` 比對結果配置器類別。

`Elem` 要符合的項目類型。 在一般情況下，這會是 string、wstring、char* 或 wchar_t\*。

`RXtraits` 項目的 traits 類別。

`Alloc2` 規則運算式配置器類別。

`IOtraits` 字串特性類別。

`IOalloc` 字串配置器類別。

`flags` 比對的旗標。

`first` 要比對之序列的開頭。

`last` 要比對之序列的結尾。

`match` 比對結果。 對應至 Elem 類型：[smatch](../standard-library/regex-typedefs.md#smatch) (針對 string)、[wsmatch](../standard-library/regex-typedefs.md#wsmatch) (針對 wstring)、[cmatch](../standard-library/regex-typedefs.md#cmatch) (針對 char*)，或 [wcmatch](../standard-library/regex-typedefs.md#wcmatch) (針對 wchar_t\*)。

`ptr` 要比對之序列開頭的指標。 如果 ptr 為 char*，則請使用 cmatch 和 regex。 如果 ptr 為 wchar_t\*，則使用 wcmatch 和 wregex。

`re` 要比對的規則運算式。 輸入 `regex` (針對 string 和 char*) 或 `wregex` (針對 wstring 和 wchar_t\*)。

`str` 要比對的字串。 對應至類型 Elem。

### <a name="remarks"></a>備註

只有在整個運算元序列 `str` 完全符合規則運算式引數 `re` 時，每個範本函式才會傳回 true。 使用 [regex_search](../standard-library/regex-functions.md#regex_search) 來比對目標序列內的子字串，以及使用 regex_iterator 來尋找多個相符項。 使用 `match_results` 物件的函式會設定其成員，以反映比對是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

使用 `match_results` 物件的函式會設定其成員，以反映比對是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

**(1):**

### <a name="example"></a>範例

```cpp
#include "stdafx.h"
#include <regex>
#include <iostream>

using namespace std;

int _tmain(int argc, _TCHAR* argv[])
{

    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);

    // (1) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (2) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal
    found = regex_match(target2.cbegin(), target2.cend(), rx2);

    // (3) with wchar_t*
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

`OutIt` 取代項目的迭代器類型。

`BidIt` 子相符項目的迭代器類型。

`RXtraits` 項目的 traits 類別。

`Alloc` 規則運算式配置器類別。

`Elem` 要符合的項目類型。

`flags` 比對的旗標。

`first` 要比對之序列的開頭。

`fmt` 取代項目的格式。

`last` 要比對之序列的結尾。

`out` 輸出迭代器。

`re` 要比對的規則運算式。

`str` 要比對的字串。

### <a name="remarks"></a>備註

第一個函式會建構 [regex_iterator 類別](../standard-library/regex-iterator-class.md)的物件 `iter(first, last, re, flags)`，並使用它來將其輸入範圍 `[first, last)` 分割為一系列的子序列 `T0M0T1M1...TN-1MN-1TN`，其中 `Mn` 是迭代器偵測到的 `nth` 相符項。 如果找不到相符項，`T0` 是整個輸入範圍且 `N` 為零。 如果 `(flags & format_first_only) != 0`，就只會使用第一個相符項、`T1` 是緊接在相符項之後的所有輸入文字，而 `N` 為 1。 針對 `[0, N)` 範圍中的每個 `i`，如果 `(flags & format_no_copy) == 0`，就會將 `Ti` 範圍中的文字複製到迭代器 `out`。 然後呼叫 `m.format(out, fmt, flags)`，其中 `m` 是子序列 `Mi` 的 `iter` 迭代器物件所傳回的 `match_results` 物件。 最後，如果 `(flags & format_no_copy) == 0`，就會將 `TN` 範圍中的文字複製到迭代器 `out`。 函式會傳回 `out`。

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

`BidIt` 子相符項目的迭代器類型。

`Alloc` 比對結果配置器類別。

`Elem` 要符合的項目類型。

`RXtraits` 項目的 traits 類別。

`Alloc2` 規則運算式配置器類別。

`IOtraits` 字串特性類別。

`IOalloc` 字串配置器類別。

`flags` 比對的旗標。

`first` 要比對之序列的開頭。

`last` 要比對之序列的結尾。

`match` 比對結果。

`ptr` 要比對之序列開頭的指標。

`re` 要比對的規則運算式。

`str` 要比對的字串。

### <a name="remarks"></a>備註

每個範本函式只有在其運算元序列中成功搜尋到規則運算式引數 `re` 時才會傳回 true。 使用 `match_results` 物件的函式會設定其成員，以反映搜尋是否成功，而且，如果成功，規則運算式中的各種擷取群組會擷取到什麼。

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

交換兩個 basic_regex 或 match_results 物件。

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) throw();

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) throw();
```

### <a name="parameters"></a>參數

`Elem` 要符合的項目類型。

`RXtraits` 項目的 traits 類別。

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

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 類別](../standard-library/regex-constants-class.md)<br/>
[regex_error 類別](../standard-library/regex-error-class.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
