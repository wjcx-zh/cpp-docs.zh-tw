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
ms.openlocfilehash: 49c2bb3f09b352413fd9f471a5ff887caa7e0238
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839747"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

[cmatch](#cmatch)\
[cRegEx_iterator](#cregex_iterator)\
[cRegEx_token_iterator](#cregex_token_iterator)\
[csub_match](#csub_match)\
[Regex](#regex)\
[smatch](#smatch)\
[sRegEx_iterator](#sregex_iterator)\
[sRegEx_token_iterator](#sregex_token_iterator)\
[ssub_match](#ssub_match)\
[wcmatch](#wcmatch)\
[wcRegEx_iterator](#wcregex_iterator)\
[wcRegEx_token_iterator](#wcregex_token_iterator)\
[wcsub_match](#wcsub_match)\
[wRegEx](#wregex)\
[wsmatch](#wsmatch)\
[wsRegEx_iterator](#wsregex_iterator)\
[wsRegEx_token_iterator](#wsregex_token_iterator)\
[wssub_match](#wssub_match)

## <a name="cmatch-typedef"></a><a name="cmatch"></a> cmatch Typedef

char match_results 的類型定義。

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Match_results 類別](../standard-library/match-results-class.md) 的特製化 `const char*` 。

## <a name="cregex_iterator-typedef"></a><a name="cregex_iterator"></a> cRegEx_iterator Typedef

char regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_iterator 類別](../standard-library/regex-iterator-class.md) 的特製化 `const char*` 。

## <a name="cregex_token_iterator-typedef"></a><a name="cregex_token_iterator"></a> cRegEx_token_iterator Typedef

Char regex_token_iterator 的類型定義

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md) 的特製化 `const char*` 。

## <a name="csub_match-typedef"></a><a name="csub_match"></a> csub_match Typedef

char sub_match 的類型定義。

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Sub_match 類別](../standard-library/sub-match-class.md) 的特製化 `const char*` 。

## <a name="regex-typedef"></a><a name="regex"></a> RegEx Typedef

char basic_regex 的類型定義。

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>備註

此類型會針對類型的元素，描述類別樣板 [Basic_RegEx 類別](../standard-library/basic-regex-class.md) 的特製化 **`char`** 。

> [!NOTE]
> 高位元字元搭配 `regex` 將會有未預期的結果。 超出 0 到 127 範圍以外的值可能會導致未定義的行為。

## <a name="smatch-typedef"></a><a name="smatch"></a> smatch Typedef

string match_results 的類型定義。

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Match_results 類別](../standard-library/match-results-class.md) 的特製化 `string::const_iterator` 。

## <a name="sregex_iterator-typedef"></a><a name="sregex_iterator"></a> sRegEx_iterator Typedef

string regex_iterator 的類型定義。

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_iterator 類別](../standard-library/regex-iterator-class.md) 的特製化 `string::const_iterator` 。

## <a name="sregex_token_iterator-typedef"></a><a name="sregex_token_iterator"></a> sRegEx_token_iterator Typedef

string regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md) 的特製化 `string::const_iterator` 。

## <a name="ssub_match-typedef"></a><a name="ssub_match"></a> ssub_match Typedef

string sub_match 的類型定義。

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Sub_match 類別](../standard-library/sub-match-class.md) 的特製化 `string::const_iterator` 。

## <a name="wcmatch-typedef"></a><a name="wcmatch"></a> wcmatch Typedef

wchar_t match_results 的類型定義。

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Match_results 類別](../standard-library/match-results-class.md) 的特製化 `const wchar_t*` 。

## <a name="wcregex_iterator-typedef"></a><a name="wcregex_iterator"></a> wcRegEx_iterator Typedef

wchar_t regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_iterator 類別](../standard-library/regex-iterator-class.md) 的特製化 `const wchar_t*` 。

## <a name="wcregex_token_iterator-typedef"></a><a name="wcregex_token_iterator"></a> wcRegEx_token_iterator Typedef

wchar_t regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md) 的特製化 `const wchar_t*` 。

## <a name="wcsub_match-typedef"></a><a name="wcsub_match"></a> wcsub_match Typedef

wchar_t sub_match 的類型定義。

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Sub_match 類別](../standard-library/sub-match-class.md) 的特製化 `const wchar_t*` 。

## <a name="wregex-typedef"></a><a name="wregex"></a> wRegEx Typedef

wchar_t basic_regex 的類型定義。

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>備註

此類型會針對類型的元素，描述類別樣板 [Basic_RegEx 類別](../standard-library/basic-regex-class.md) 的特製化 **`wchar_t`** 。

## <a name="wsmatch-typedef"></a><a name="wsmatch"></a> wsmatch Typedef

wstring match_results 的類型定義。

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Match_results 類別](../standard-library/match-results-class.md) 的特製化 `wstring::const_iterator` 。

## <a name="wsregex_iterator-typedef"></a><a name="wsregex_iterator"></a> wsRegEx_iterator Typedef

wstring regex_iterator 的類型定義。

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_iterator 類別](../standard-library/regex-iterator-class.md) 的特製化 `wstring::const_iterator` 。

## <a name="wsregex_token_iterator-typedef"></a><a name="wsregex_token_iterator"></a> wsRegEx_token_iterator Typedef

wstring regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md) 的特製化 `wstring::const_iterator` 。

## <a name="wssub_match-typedef"></a><a name="wssub_match"></a> wssub_match Typedef

wstring sub_match 的類型定義。

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>備註

此型別描述型別的反覆運算器 [Sub_match 類別](../standard-library/sub-match-class.md) 的特製化 `wstring::const_iterator` 。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[RegEx_constants 類別](../standard-library/regex-constants-class.md)\
[RegEx_error 類別](../standard-library/regex-error-class.md)\
[\<regex> 功能](../standard-library/regex-functions.md)\
[RegEx_iterator 類別](../standard-library/regex-iterator-class.md)\
[\<regex> 運營商](../standard-library/regex-operators.md)\
[RegEx_token_iterator 類別](../standard-library/regex-token-iterator-class.md)\
[RegEx_traits 類別](../standard-library/regex-traits-class.md)
