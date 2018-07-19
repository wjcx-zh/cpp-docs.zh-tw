---
title: '&lt;regex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff0fffeffd10f382f4d0d4fe6361c2eddac55e3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963127"
---
# <a name="ltregexgt"></a>&lt;regex&gt;

定義範本類別來剖析[規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)，以及定義數個範本類別和函式來搜尋與規則運算式物件相符的文字。

## <a name="syntax"></a>語法

```cpp
#include <regex>
```

## <a name="remarks"></a>備註

若要建立規則運算式物件，請使用範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)或它的其中一個特製化 ([regex](../standard-library/regex-typedefs.md#regex) 和 [wregex](../standard-library/regex-typedefs.md#wregex))，並與 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type) 類型的語法旗標搭配使用。

若要搜尋與規則運算式物件相符的文字，請使用 範本函式[regex_match](../standard-library/regex-functions.md#regex_match)並[regex_search](../standard-library/regex-functions.md#regex_search)連同類型的相符旗標[regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type)。 這些函式會使用範本類別 [match_results 類別](../standard-library/match-results-class.md)及其特製化 ([cmatch](../standard-library/regex-typedefs.md#cmatch)、[wcmatch](../standard-library/regex-typedefs.md#wcmatch)、[smatch](../standard-library/regex-typedefs.md#smatch) 及 [wsmatch](../standard-library/regex-typedefs.md#wsmatch)) 傳回結果，並與範本類別 [sub_match 類別](../standard-library/sub-match-class.md)及其特製化 ([csub_match](../standard-library/regex-typedefs.md#csub_match)、[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)、[ssub_match](../standard-library/regex-typedefs.md#ssub_match) 及 [wssub_match](../standard-library/regex-typedefs.md#wssub_match)) 搭配使用。

若要取代與規則運算式物件相符的文字，請使用 範本函數[regex_replace](../standard-library/regex-functions.md#regex_replace)連同類型的相符旗標[regex_constants::](../standard-library/regex-constants-class.md#match_flag_type)。

若要逐一查看規則運算式物件的多個相符項目，請使用範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)和 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)或它的其中一個特製化 ([cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)、[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)、[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)、[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator)、[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)、[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)、[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator) 或 [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator))，並與 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#match_flag_type) 類型的相符旗標搭配使用。

若要修改規則運算式文法的詳細資訊，請撰寫實作規則運算式特性的類別。

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_regex](../standard-library/basic-regex-class.md)|包裝規則運算式。|
|[match_results](../standard-library/match-results-class.md)|保留子相符項目的序列。|
|[regex_constants](../standard-library/regex-constants-class.md)|保留各種常數。|
|[regex_error](../standard-library/regex-error-class.md)|報告錯誤的規則運算式。|
|[regex_iterator](../standard-library/regex-iterator-class.md)|逐一查看相符的結果。|
|[regex_traits](../standard-library/regex-traits-class.md)|描述進行比對的元素特性。|
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|描述的特性**char**進行比對。|
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|描述的特性**wchar_t**進行比對。|
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|逐一查看子相符項目。|
|[sub_match](../standard-library/sub-match-class.md)|描述子相符項目。|

### <a name="type-definitions"></a>類型定義

|||
|-|-|
|[cmatch](../standard-library/regex-typedefs.md#cmatch)|類型定義**char** `match_results`。|
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator)|類型定義**char** `regex_iterator`。|
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator)|類型定義**char** `regex_token_iterator`。|
|[csub_match](../standard-library/regex-typedefs.md#csub_match)|類型定義**char** `sub_match`。|
|[regex](../standard-library/regex-typedefs.md#regex)|類型定義**char** `basic_regex`。|
|[smatch](../standard-library/regex-typedefs.md#smatch)|`string` `match_results` 的類型定義。|
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator)|`string` `regex_iterator` 的類型定義。|
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator)|`string` `regex_token_iterator` 的類型定義。|
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match)|`string` `sub_match` 的類型定義。|
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch)|類型定義**wchar_t** `match_results`。|
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator)|類型定義**wchar_t** `regex_iterator`。|
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator)|類型定義**wchar_t** `regex_token_iterator`。|
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match)|類型定義**wchar_t** `sub_match`。|
|[wregex](../standard-library/regex-typedefs.md#wregex)|類型定義**wchar_t** `basic_regex`。|
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

[規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)<br/>
[regex_constants 類別](../standard-library/regex-constants-class.md)<br/>
[regex_error 類別](../standard-library/regex-error-class.md)<br/>
[\<regex> 函式](../standard-library/regex-functions.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
