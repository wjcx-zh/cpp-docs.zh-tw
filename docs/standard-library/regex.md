---
title: '&lt;regex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: 4e172f8bf72fd528027c333cf411a307aa97d786
ms.lasthandoff: 02/24/2017

---
# <a name="ltregexgt"></a>&lt;regex&gt;
定義範本類別來剖析[規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)，以及定義數個範本類別和函式來搜尋與規則運算式物件相符的文字。  
  
## <a name="syntax"></a>語法  
  
```  
#include <regex>  
```  
  
## <a name="remarks"></a>備註  
 若要建立規則運算式物件，請使用範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)或它的其中一個特製化 ([regex](../standard-library/regex-typedefs.md#regex_typedef) 和 [wregex](../standard-library/regex-typedefs.md#wregex_typedef))，並與 [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#regex_constants__syntax_option_type) 類型的語法旗標搭配使用。  
  
 若要搜尋與規則運算式物件相符的文字，請使用範本函式 [regex_match 函式](../standard-library/regex-functions.md#regex_match_function)和 [regex_search 函式](../standard-library/regex-functions.md#regex_search_function)，並與 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type) 類型的相符旗標搭配使用。 這些函式會使用範本類別 [match_results 類別](../standard-library/match-results-class.md)及其特製化 ([cmatch](../standard-library/regex-typedefs.md#cmatch_typedef)、[wcmatch](../standard-library/regex-typedefs.md#wcmatch_typedef)、[smatch](../standard-library/regex-typedefs.md#smatch_typedef) 及 [wsmatch](../standard-library/regex-typedefs.md#wsmatch_typedef)) 傳回結果，並與範本類別 [sub_match 類別](../standard-library/sub-match-class.md)及其特製化 ([csub_match](../standard-library/regex-typedefs.md#csub_match_typedef)、[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match_typedef)、[ssub_match](../standard-library/regex-typedefs.md#ssub_match_typedef) 及 [wssub_match](../standard-library/regex-typedefs.md#wssub_match_typedef)) 搭配使用。  
  
 若要取代與規則運算式物件相符的文字，請使用範本函式 [regex_replace 函式](../standard-library/regex-functions.md#regex_replace_function)，並與 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type) 類型的相符旗標搭配使用。  
  
 若要逐一查看規則運算式物件的多個相符項目，請使用範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)和 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)或它的其中一個特製化 ([cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator_typedef)、[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator_typedef)、[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator_typedef)、[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator_typedef)、[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator_typedef)、[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator_typedef)、[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator_typedef) 或 [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator_typedef))，並與 [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type) 類型的相符旗標搭配使用。  
  
 若要修改規則運算式文法的詳細資訊，請撰寫實作規則運算式特性的類別。  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[basic_regex](../standard-library/basic-regex-class.md)|包裝規則運算式。|  
|[match_results](../standard-library/match-results-class.md)|保留子相符項目的序列。|  
|[regex_constants](../standard-library/regex-constants-class.md)|保留各種常數。|  
|[regex_error](../standard-library/regex-error-class.md)|報告錯誤的規則運算式。|  
|[regex_iterator](../standard-library/regex-iterator-class.md)|逐一查看相符的結果。|  
|[regex_traits](../standard-library/regex-traits-class.md)|描述進行比對的元素特性。|  
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|描述進行比對的 `char` 特性。|  
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|描述進行比對的 `wchar_t` 特性。|  
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|逐一查看子相符項目。|  
|[sub_match](../standard-library/sub-match-class.md)|描述子相符項目。|  
  
### <a name="type-definitions"></a>類型定義  
  
|||  
|-|-|  
|[cmatch](../standard-library/regex-typedefs.md#cmatch_typedef)|`char``match_results` 的類型定義。|  
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator_typedef)|`char``regex_iterator` 的類型定義。|  
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator_typedef)|`char``regex_token_iterator` 的類型定義。|  
|[csub_match](../standard-library/regex-typedefs.md#csub_match_typedef)|`char``sub_match` 的類型定義。|  
|[regex](../standard-library/regex-typedefs.md#regex_typedef)|`char``basic_regex` 的類型定義。|  
|[smatch](../standard-library/regex-typedefs.md#smatch_typedef)|`string``match_results` 的類型定義。|  
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator_typedef)|`string``regex_iterator` 的類型定義。|  
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator_typedef)|`string``regex_token_iterator` 的類型定義。|  
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match_typedef)|`string``sub_match` 的類型定義。|  
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch_typedef)|`wchar_t``match_results` 的類型定義。|  
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator_typedef)|`wchar_t``regex_iterator` 的類型定義。|  
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator_typedef)|`wchar_t``regex_token_iterator` 的類型定義。|  
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match_typedef)|`wchar_t``sub_match` 的類型定義。|  
|[wregex](../standard-library/regex-typedefs.md#wregex_typedef)|`wchar_t``basic_regex` 的類型定義。|  
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch_typedef)|`wstring``match_results` 的類型定義。|  
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator_typedef)|`wstring``regex_iterator` 的類型定義。|  
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator_typedef)|`wstring``regex_token_iterator` 的類型定義。|  
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match_typedef)|`wstring``sub_match` 的類型定義。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[regex_match](../standard-library/regex-functions.md#regex_match_function)|完全符合規則運算式。|  
|[regex_replace](../standard-library/regex-functions.md#regex_replace_function)|取代符合的規則運算式。|  
|[regex_search](../standard-library/regex-functions.md#regex_search_function)|搜尋規則運算式相符項目。|  
|[swap](../standard-library/regex-functions.md#swap_function)|交換 `basic_regex` 或 `match_results` 物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator==](../standard-library/regex-operators.md#operator_eq_eq)|不同物件的比較 (等於)。|  
|[operator!=](../standard-library/regex-operators.md#operator_neq)|不同物件的比較 (不等於)。|  
|[operator<](../standard-library/regex-operators.md#operator_lt_)|不同物件的比較 (小於)。|  
|[operator\<=](../standard-library/regex-operators.md#operator_lt__eq)|不同物件的比較 (小於或等於)。|  
|[operator>](../standard-library/regex-operators.md#operator_gt_)|不同物件的比較 (大於)。|  
|[operator>=](../standard-library/regex-operators.md#operator_gt__eq)|不同物件的比較 (大於或等於)。|  
|[operator<<](../standard-library/regex-operators.md#operator_lt__lt_)|在資料流中插入 `sub_match`。|  
  
## <a name="see-also"></a>另請參閱  
[規則運算式 (C++)](../standard-library/regular-expressions-cpp.md)  
[regex_constants 類別](../standard-library/regex-constants-class.md)  
[regex_error 類別](../standard-library/regex-error-class.md)  
[\<regex> 函式](../standard-library/regex-functions.md)  
[regex_iterator 類別](../standard-library/regex-iterator-class.md)  
[\<regex> 運算子](../standard-library/regex-operators.md)  
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)  
[regex_traits 類別](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  




