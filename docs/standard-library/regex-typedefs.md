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
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419571"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>  cmatch Typedef

char match_results 的類型定義。

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>備註

此類型描述 `const char*`類型反覆運算器的類別樣板[Match_results 類別](../standard-library/match-results-class.md)的特製化。

## <a name="cregex_iterator"></a>  cregex_iterator Typedef

char regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `const char*`類型反覆運算器的類別樣板[Regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。

## <a name="cregex_token_iterator"></a>  cregex_token_iterator Typedef

Char regex_token_iterator 的類型定義

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `const char*`類型反覆運算器的類別樣板[Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。

## <a name="csub_match"></a>  csub_match Typedef

char sub_match 的類型定義。

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>備註

此類型描述 `const char*`類型反覆運算器的類別樣板[Sub_match 類別](../standard-library/sub-match-class.md)的特製化。

## <a name="regex"></a>  regex Typedef

char basic_regex 的類型定義。

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>備註

此類型描述類別樣板的特製化， [Basic_RegEx 類別](../standard-library/basic-regex-class.md)用於類型為**char**的元素。

> [!NOTE]
> 高位元字元搭配 `regex` 將會有未預期的結果。 超出 0 到 127 範圍以外的值可能會導致未定義的行為。

## <a name="smatch"></a>  smatch Typedef

string match_results 的類型定義。

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>備註

此類型描述 `string::const_iterator`類型反覆運算器的類別樣板[Match_results 類別](../standard-library/match-results-class.md)的特製化。

## <a name="sregex_iterator"></a>  sregex_iterator Typedef

string regex_iterator 的類型定義。

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `string::const_iterator`類型反覆運算器的類別樣板[Regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。

## <a name="sregex_token_iterator"></a>  sregex_token_iterator Typedef

string regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `string::const_iterator`類型反覆運算器的類別樣板[Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。

## <a name="ssub_match"></a>  ssub_match Typedef

string sub_match 的類型定義。

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>備註

此類型描述 `string::const_iterator`類型反覆運算器的類別樣板[Sub_match 類別](../standard-library/sub-match-class.md)的特製化。

## <a name="wcmatch"></a>  wcmatch Typedef

wchar_t match_results 的類型定義。

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>備註

此類型描述 `const wchar_t*`類型反覆運算器的類別樣板[Match_results 類別](../standard-library/match-results-class.md)的特製化。

## <a name="wcregex_iterator"></a>  wcregex_iterator Typedef

wchar_t regex_iterator 的類型定義。

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `const wchar_t*`類型反覆運算器的類別樣板[Regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator Typedef

wchar_t regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `const wchar_t*`類型反覆運算器的類別樣板[Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。

## <a name="wcsub_match"></a>  wcsub_match Typedef

wchar_t sub_match 的類型定義。

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>備註

此類型描述 `const wchar_t*`類型反覆運算器的類別樣板[Sub_match 類別](../standard-library/sub-match-class.md)的特製化。

## <a name="wregex"></a>  wregex Typedef

wchar_t basic_regex 的類型定義。

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>備註

此類型描述類別樣板的特製化， [Basic_RegEx 類別](../standard-library/basic-regex-class.md)，適用于**wchar_t**類型的元素。

## <a name="wsmatch"></a>  wsmatch Typedef

wstring match_results 的類型定義。

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>備註

此類型描述 `wstring::const_iterator`類型反覆運算器的類別樣板[Match_results 類別](../standard-library/match-results-class.md)的特製化。

## <a name="wsregex_iterator"></a>  wsregex_iterator Typedef

wstring regex_iterator 的類型定義。

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `wstring::const_iterator`類型反覆運算器的類別樣板[Regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator Typedef

wstring regex_token_iterator 的類型定義。

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>備註

此類型描述 `wstring::const_iterator`類型反覆運算器的類別樣板[Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。

## <a name="wssub_match"></a>  wssub_match Typedef

wstring sub_match 的類型定義。

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>備註

此類型描述 `wstring::const_iterator`類型反覆運算器的類別樣板[Sub_match 類別](../standard-library/sub-match-class.md)的特製化。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)\
[Regex_constants 類別](../standard-library/regex-constants-class.md)\
[Regex_error 類別](../standard-library/regex-error-class.md)\
[\<RegEx > 函數](../standard-library/regex-functions.md)\
[Regex_iterator 類別](../standard-library/regex-iterator-class.md)\
[\<RegEx > 運算子](../standard-library/regex-operators.md)\
[Regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)\
[regex_traits 類別](../standard-library/regex-traits-class.md)
