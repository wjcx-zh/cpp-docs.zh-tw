---
title: "&lt;regex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<regex>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex 標頭 [TR1]"
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# &lt;regex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義範本類別來剖析[規則運算式 \(C\+\+\)](../standard-library/regular-expressions-cpp.md)，以及定義數個範本類別和函式，藉此搜尋和規則運算式物件相符的文字。  
  
## 語法  
  
```  
#include <regex>  
```  
  
## 備註  
 若要建立規則運算式物件，請使用此範本類別 [basic\_regex 類別](../standard-library/basic-regex-class.md) 或其特製化 \([regex Typedef](../Topic/regex%20Typedef.md) 和 [wregex Typedef](../Topic/wregex%20Typedef.md)\)，並與 [regex\_constants::syntax\_option\_type](../Topic/regex_constants::syntax_option_type.md) 類型的語法旗標搭配使用。  
  
 若要搜尋與規則運算式物件相符的文字，請使用此範本函式 [regex\_match 函式](../Topic/regex_match%20Function.md) 和 [regex\_search 函式](../Topic/regex_search%20Function.md)，並與[regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 類型的相符旗標搭配使用。  這些函式使用此範本類別 [match\_results 類別](../standard-library/match-results-class.md) 和其特製化 \([cmatch Typedef](../Topic/cmatch%20Typedef.md)、[wcmatch Typedef](../Topic/wcmatch%20Typedef.md)、[smatch Typedef](../Topic/smatch%20Typedef.md) 和 [wsmatch Typedef](../Topic/wsmatch%20Typedef.md)\) 傳回結果，並與此範本類別 [sub\_match 類別](../standard-library/sub-match-class.md) 和其特製化 \([csub\_match Typedef](../Topic/csub_match%20Typedef.md)、[wcsub\_match Typedef](../Topic/wcsub_match%20Typedef.md)、[ssub\_match Typedef](../Topic/ssub_match%20Typedef.md) 和 [wssub\_match Typedef](../Topic/wssub_match%20Typedef.md)\) 搭配使用。  
  
 若要取代與規則運算式物件相符的文字，請使用此範本函式 [regex\_replace 函式](../Topic/regex_replace%20Function.md)，並與 [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 類型的相符旗標搭配使用。  
  
 若要逐一查看規則運算式物件的多個相符項目，請使用此範本類別 [regex\_iterator 類別](../standard-library/regex-iterator-class.md) 和 [regex\_token\_iterator 類別](../standard-library/regex-token-iterator-class.md) 或其特製化 \([cregex\_iterator Typedef](../Topic/cregex_iterator%20Typedef.md)、[sregex\_iterator Typedef](../Topic/sregex_iterator%20Typedef.md)、[wcregex\_iterator Typedef](../Topic/wcregex_iterator%20Typedef.md)、[wsregex\_iterator Typedef](../Topic/wsregex_iterator%20Typedef.md)、[cregex\_token\_iterator Typedef](../Topic/cregex_token_iterator%20Typedef.md)、[sregex\_token\_iterator Typedef](../Topic/sregex_token_iterator%20Typedef.md)、[wcregex\_token\_iterator Typedef](../Topic/wcregex_token_iterator%20Typedef.md) 或 [wsregex\_token\_iterator Typedef](../Topic/wsregex_token_iterator%20Typedef.md)\)，並與類型 [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md) 的相符旗標搭配使用。  
  
 若要修改規則運算式文法的詳細資訊，請撰寫實作規則運算式特性的類別。  
  
### 類別  
  
|||  
|-|-|  
|[basic\_regex](../standard-library/basic-regex-class.md)|包裝規則運算式。|  
|[match\_results](../standard-library/match-results-class.md)|保留子相符項目的序列。|  
|[regex\_constants](../standard-library/regex-constants-class.md)|保留各種常數。|  
|[regex\_error](../standard-library/regex-error-class.md)|報告錯誤的規則運算式。|  
|[regex\_iterator](../standard-library/regex-iterator-class.md)|逐一查看相符的結果。|  
|[regex\_traits](../standard-library/regex-traits-class.md)|描述進行比對的項目特性。|  
|[regex\_traits\<char\>](../standard-library/regex-traits-char-class.md)|描述進行比對的 `char` 特性。|  
|[regex\_traits\<wchar\_t\>](../standard-library/regex-traits-wchar-t-class.md)|描述進行比對的 `wchar_t` 特性。|  
|[regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)|逐一查看子相符項目。|  
|[sub\_match](../standard-library/sub-match-class.md)|描述子相符項目。|  
  
### 類型定義  
  
|||  
|-|-|  
|[cmatch](../Topic/cmatch%20Typedef.md)|`char` `match_results` 的類型定義。|  
|[cregex\_iterator](../Topic/cregex_iterator%20Typedef.md)|`char` `regex_iterator` 的類型定義。|  
|[cregex\_token\_iterator](../Topic/cregex_token_iterator%20Typedef.md)|`char` `regex_token_iterator` 的類型定義。|  
|[csub\_match](../Topic/csub_match%20Typedef.md)|`char` `sub_match` 的類型定義。|  
|[regex](../Topic/regex%20Typedef.md)|`char` `basic_regex` 的類型定義。|  
|[smatch](../Topic/smatch%20Typedef.md)|`string` `match_results` 的類型定義。|  
|[sregex\_iterator](../Topic/sregex_iterator%20Typedef.md)|`string` `regex_iterator` 的類型定義。|  
|[sregex\_token\_iterator](../Topic/sregex_token_iterator%20Typedef.md)|`string` `regex_token_iterator` 的類型定義。|  
|[ssub\_match](../Topic/ssub_match%20Typedef.md)|`string` `sub_match` 的類型定義。|  
|[wcmatch](../Topic/wcmatch%20Typedef.md)|`wchar_t` `match_results` 的類型定義。|  
|[wcregex\_iterator](../Topic/wcregex_iterator%20Typedef.md)|`wchar_t` `regex_iterator` 的類型定義。|  
|[wcregex\_token\_iterator](../Topic/wcregex_token_iterator%20Typedef.md)|`wchar_t` `regex_token_iterator` 的類型定義。|  
|[wcsub\_match](../Topic/wcsub_match%20Typedef.md)|`wchar_t` `sub_match` 的類型定義。|  
|[wregex](../Topic/wregex%20Typedef.md)|`wchar_t` `basic_regex` 的類型定義。|  
|[wsmatch](../Topic/wsmatch%20Typedef.md)|`wstring` `match_results` 的類型定義。|  
|[wsregex\_iterator](../Topic/wsregex_iterator%20Typedef.md)|`wstring` `regex_iterator` 的類型定義。|  
|[wsregex\_token\_iterator](../Topic/wsregex_token_iterator%20Typedef.md)|`wstring` `regex_token_iterator` 的類型定義。|  
|[wssub\_match](../Topic/wssub_match%20Typedef.md)|`wstring` `sub_match` 的類型定義。|  
  
### 函式  
  
|||  
|-|-|  
|[regex\_match](../Topic/regex_match%20Function.md)|完全符合規則運算式。|  
|[regex\_replace](../Topic/regex_replace%20Function.md)|取代符合的規則運算式。|  
|[regex\_search](../Topic/regex_search%20Function.md)|搜尋規則運算式相符項目。|  
|[交換](../Topic/swap%20Function%20%3Cregex%3E.md)|交換 `basic_regex` 或 `match_results` 物件。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/operator==%20%3Cregex%3E.md)|不同物件的比較 \(等於\)。|  
|[operator\!\=](../Topic/operator!=%20%3Cregex%3E.md)|不同物件的比較 \(不等於\)。|  
|[運算子 \<](../Topic/operator%3C%20%3Cregex%3E.md)|不同物件的比較 \(小於\)。|  
|[運算子 \<\=](../Topic/operator%3C=%20%3Cregex%3E.md)|不同物件的比較 \(小於或等於\)。|  
|[運算子 \>](../Topic/operator%3E%20%3Cregex%3E.md)|不同物件的比較 \(大於\)。|  
|[運算子 \>\=](../Topic/operator%3E=%20%3Cregex%3E.md)|不同物件的比較 \(大於或等於\)。|  
|[運算子 \<\<](../Topic/operator%3C%3C%20%3Cregex%3E.md)|在資料流中插入 `sub_match`。|  
  
## 請參閱  
 [規則運算式 \(C\+\+\)](../standard-library/regular-expressions-cpp.md)