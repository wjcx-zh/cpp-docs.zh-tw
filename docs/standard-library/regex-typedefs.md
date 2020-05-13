---
title: '&lt;regex&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 5dbda2df4877da7594dd633e9f203a3780b4adb1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368550"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[Regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch-typedef"></a><a name="cmatch"></a>cmatch 類型 def

char match_results 的類型定義。

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的預設[match_results類別](../standard-library/match-results-class.md)的類型的運算器`const char*`。

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a>cregex_iterator類型 def

char regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的設定[regex_iterator類別](../standard-library/regex-iterator-class.md)的型態的運算`const char*`器 。

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a>cregex_token_iterator類型 def

Char regex_token_iterator 的類型定義

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>備註

這個類型描述了類別的資訊的設定[regex_token_iterator類別](../standard-library/regex-token-iterator-class.md)的型態的運算`const char*`器 。

## <a name="csub_match-typedef"></a><a name="csub_match"></a>csub_match型態def

char sub_match 的類型定義。

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的一[個資訊 sub_match類別](../standard-library/sub-match-class.md)的型態`const char*`的運算器 。

## <a name="regex-typedef"></a><a name="regex"></a>正規類型def

char basic_regex 的類型定義。

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>備註

該類型描述了類範本的專門化[basic_regex類](../standard-library/basic-regex-class.md)類型**字元**的元素。

> [!NOTE]
> 高位元字元搭配 `regex` 將會有未預期的結果。 超出 0 到 127 範圍以外的值可能會導致未定義的行為。

## <a name="smatch-typedef"></a><a name="smatch"></a>比賽類型def

string match_results 的類型定義。

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的預設[match_results類別](../standard-library/match-results-class.md)的類型的運算器`string::const_iterator`。

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a>sregex_iterator類型def

string regex_iterator 的類型定義。

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的設定[regex_iterator類別](../standard-library/regex-iterator-class.md)的型態的運算`string::const_iterator`器 。

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a>sregex_token_iterator類型 def

string regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>備註

這個類型描述了類別的資訊的設定[regex_token_iterator類別](../standard-library/regex-token-iterator-class.md)的型態的運算`string::const_iterator`器 。

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a>ssub_match類型 def

string sub_match 的類型定義。

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的一[個資訊 sub_match類別](../standard-library/sub-match-class.md)的型態`string::const_iterator`的運算器 。

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a>wcmatch 類型 def

wchar_t match_results 的類型定義。

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的預設[match_results類別](../standard-library/match-results-class.md)的類型的運算器`const wchar_t*`。

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a>wcregex_iterator類型 def

wchar_t regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的設定[regex_iterator類別](../standard-library/regex-iterator-class.md)的型態的運算`const wchar_t*`器 。

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a>wcregex_token_iterator型態 def

wchar_t regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>備註

這個類型描述了類別的資訊的設定[regex_token_iterator類別](../standard-library/regex-token-iterator-class.md)的型態的運算`const wchar_t*`器 。

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a>wcsub_match型態 def

wchar_t sub_match 的類型定義。

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的一[個資訊 sub_match類別](../standard-library/sub-match-class.md)的型態`const wchar_t*`的運算器 。

## <a name="wregex-typedef"></a><a name="wregex"></a>wregex 類型 def

wchar_t basic_regex 的類型定義。

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>備註

該類型描述了類範本[basic_regex類](../standard-library/basic-regex-class.md)的專門化 **,wchar_t**類型元素。

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a>wsmatch 類型 def

wstring match_results 的類型定義。

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的預設[match_results類別](../standard-library/match-results-class.md)的類型的運算器`wstring::const_iterator`。

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a>wsregex_iterator類型

wstring regex_iterator 的類型定義。

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的設定[regex_iterator類別](../standard-library/regex-iterator-class.md)的型態的運算`wstring::const_iterator`器 。

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a>wsregex_token_iterator類型def

wstring regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>備註

這個類型描述了類別的資訊的設定[regex_token_iterator類別](../standard-library/regex-token-iterator-class.md)的型態的運算`wstring::const_iterator`器 。

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a>wssub_match類型def

wstring sub_match 的類型定義。

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>備註

此類型描述了類別的樣本的一[個資訊 sub_match類別](../standard-library/sub-match-class.md)的型態`wstring::const_iterator`的運算器 。

## <a name="see-also"></a>另請參閱

[\<正則>](../standard-library/regex.md)\
[regex_constants類](../standard-library/regex-constants-class.md)\
[regex_error類](../standard-library/regex-error-class.md)\
[\<正規表示式>函數](../standard-library/regex-functions.md)\
[regex_iterator類](../standard-library/regex-iterator-class.md)\
[\<正則>運算子](../standard-library/regex-operators.md)\
[regex_token_iterator類](../standard-library/regex-token-iterator-class.md)\
[regex_traits 類別](../standard-library/regex-traits-class.md)
