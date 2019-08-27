---
title: '&lt;regex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <regex>
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
ms.openlocfilehash: 3e3f3b49b3672042e0376e7738a8cf8924e1c2a8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451439"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

定義範本類別來剖析[規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)，以及定義數個範本類別和函式來搜尋與規則運算式物件相符的文字。

## <a name="syntax"></a>語法

```cpp
#include <regex>
```

## <a name="remarks"></a>備註

若要建立規則運算式物件，請使用範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)或它的其中一個特製化 ([regex](../standard-library/regex-typedefs.md#regex) 和 [wregex](../standard-library/regex-typedefs.md#wregex))，並與 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 類型的語法旗標搭配使用。

若要搜尋與正則運算式物件相符的文字, 請使用樣板函式[RegEx_match](../standard-library/regex-functions.md#regex_match)和[RegEx_search](../standard-library/regex-functions.md#regex_search), 以及[RegEx_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type)類型的 match 旗標。 這些函式會使用範本類別 [match_results 類別](../standard-library/match-results-class.md)及其特製化 ([cmatch](../standard-library/regex-typedefs.md#cmatch)、[wcmatch](../standard-library/regex-typedefs.md#wcmatch)、[smatch](../standard-library/regex-typedefs.md#smatch) 及 [wsmatch](../standard-library/regex-typedefs.md#wsmatch)) 傳回結果，並與範本類別 [sub_match 類別](../standard-library/sub-match-class.md)及其特製化 ([csub_match](../standard-library/regex-typedefs.md#csub_match)、[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)、[ssub_match](../standard-library/regex-typedefs.md#ssub_match) 及 [wssub_match](../standard-library/regex-typedefs.md#wssub_match)) 搭配使用。

若要取代符合正則運算式物件的文字, 請使用範本函式[RegEx_replace](../standard-library/regex-functions.md#regex_replace), 以及[RegEx_constants:: match_flag_type](../standard-library/regex-constants-class.md#match_flag_type)類型的比對旗標。

若要逐一查看規則運算式物件的多個相符項目，請使用範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)和 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)或它的其中一個特製化 ([cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)、[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)、[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)、[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)、[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)、[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)、[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator) 或 [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator))，並與 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type) 類型的相符旗標搭配使用。

若要修改規則運算式文法的詳細資訊，請撰寫實作規則運算式特性的類別。

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|包裝規則運算式。|
|[match_results](../standard-library/match-results-class.md)|保留子相符項目的序列。|
|[regex_constants](../standard-library/regex-constants-class.md)|保留各種常數。|
|[regex_error](../standard-library/regex-error-class.md)|報告錯誤的規則運算式。|
|[regex_iterator](../standard-library/regex-iterator-class.md)|逐一查看相符的結果。|
|[regex_traits](../standard-library/regex-traits-class.md)|描述進行比對的元素特性。|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|描述**char**的特性以進行比對。|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|描述**wchar_t**的特性以進行比對。|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|逐一查看子相符項目。|
|[sub_match](../standard-library/sub-match-class.md)|描述子相符項目。|

### <a name="type-definitions"></a>類型定義

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)| Char`match_results`的類型定義。|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)| Char`regex_iterator`的類型定義。|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)| Char`regex_token_iterator`的類型定義。|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)| Char`sub_match`的類型定義。|
|[regex](../standard-library/regex-typedefs.md#regex)| Char`basic_regex`的類型定義。|
|[smatch](../standard-library/regex-typedefs.md#smatch)|`string` `match_results` 的類型定義。|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|`string` `regex_iterator` 的類型定義。|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|`string` `regex_token_iterator` 的類型定義。|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|`string` `sub_match` 的類型定義。|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)| Wchar_t`match_results`的類型定義。|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)| Wchar_t`regex_iterator`的類型定義。|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)| Wchar_t`regex_token_iterator`的類型定義。|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)| Wchar_t`sub_match`的類型定義。|
|[wregex](../standard-library/regex-typedefs.md#wregex)| Wchar_t`basic_regex`的類型定義。|
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch)|`wstring` `match_results` 的類型定義。|
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)|`wstring` `regex_iterator` 的類型定義。|
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator)|`wstring` `regex_token_iterator` 的類型定義。|
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match)|`wstring` `sub_match` 的類型定義。|

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[regex_match](../standard-library/regex-functions.md#regex_match)|完全符合規則運算式。|
|[regex_replace](../standard-library/regex-functions.md#regex_replace)|取代符合的規則運算式。|
|[regex_search](../standard-library/regex-functions.md#regex_search)|搜尋規則運算式相符項目。|
|[swap](../standard-library/regex-functions.md#swap)|交換 `basic_regex` 或 `match_results` 物件。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator==](../standard-library/regex-operators.md#op_eq_eq)|不同物件的比較 (等於)。|
|[operator!=](../standard-library/regex-operators.md#op_neq)|不同物件的比較 (不等於)。|
|[operator<](../standard-library/regex-operators.md#op_lt)|不同物件的比較 (小於)。|
|[operator\<=](../standard-library/regex-operators.md#op_gt_eq)|不同物件的比較 (小於或等於)。|
|[operator>](../standard-library/regex-operators.md#op_gt)|不同物件的比較 (大於)。|
|[operator>=](../standard-library/regex-operators.md#op_gt_eq)|不同物件的比較 (大於或等於)。|
|[operator<<](../standard-library/regex-operators.md#op_lt_lt)|在資料流中插入 `sub_match`。|

## <a name="see-also"></a>另請參閱

[正則運算式C++()](../standard-library/regular-expressions-cpp.md)\
[RegEx_constants 類別](../standard-library/regex-constants-class.md)\
[RegEx_error 類別](../standard-library/regex-error-class.md)\
[\<RegEx > 函式](../standard-library/regex-functions.md)\
[RegEx_iterator 類別](../standard-library/regex-iterator-class.md)\
[\<RegEx > 運算子](../standard-library/regex-operators.md)\
[RegEx_token_iterator 類別](../standard-library/regex-token-iterator-class.md)\
[RegEx_traits 類別](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
