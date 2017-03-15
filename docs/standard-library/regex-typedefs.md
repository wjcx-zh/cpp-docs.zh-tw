---
title: '&lt;regex&gt; typedefs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmatch
- std::cmatch
- regex/std::cmatch
- cregex_iterator
- std::cregex_iterator
- regex/std::cregex_iterator
- cregex_token_iterator
- std::cregex_token_iterator
- regex/std::cregex_token_iterator
- csub_match
- std::csub_match
- regex/std::csub_match
- regex
- std::regex
- regex/std::regex
- smatch
- std::smatch
- regex/std::smatch
- sregex_iterator
- std::sregex_iterator
- regex/std::sregex_iterator
- sregex_token_iterator
- std::sregex_token_iterator
- regex/std::sregex_token_iterator
- ssub_match
- std::ssub_match
- regex/std::ssub_match
- wcmatch
- std::wcmatch
- regex/std::wcmatch
- wcregex_iterator
- std::wcregex_iterator
- regex/std::wcregex_iterator
- wcregex_token_iterator
- std::wcregex_token_iterator
- regex/std::wcregex_token_iterator
- wcsub_match
- std::wcsub_match
- regex/std::wcsub_match
- wregex
- std::wregex
- regex/std::wregex
- wsmatch
- std::wsmatch
- regex/std::wsmatch
- wsregex_iterator
- std::wsregex_iterator
- regex/std::wsregex_iterator
- wsregex_token_iterator
- std::wsregex_token_iterator
- regex/std::wsregex_token_iterator
- wssub_match
- std::wssub_match
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 60822dd232399b27ccda3db829b636d817091a2d
ms.lasthandoff: 02/24/2017

---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs
||||  
|-|-|-|  
|[cmatch Typedef](#cmatch_typedef)|[cregex_iterator Typedef](#cregex_iterator_typedef)|[cregex_token_iterator Typedef](#cregex_token_iterator_typedef)|  
|[csub_match Typedef](#csub_match_typedef)|[regex Typedef](#regex_typedef)|[smatch Typedef](#smatch_typedef)|  
|[sregex_iterator Typedef](#sregex_iterator_typedef)|[sregex_token_iterator Typedef](#sregex_token_iterator_typedef)|[ssub_match Typedef](#ssub_match_typedef)|  
|[wcmatch Typedef](#wcmatch_typedef)|[wcregex_iterator Typedef](#wcregex_iterator_typedef)|[wcregex_token_iterator Typedef](#wcregex_token_iterator_typedef)|  
|[wcsub_match Typedef](#wcsub_match_typedef)|[wregex Typedef](#wregex_typedef)|[wsmatch Typedef](#wsmatch_typedef)|  
|[wsregex_iterator Typedef](#wsregex_iterator_typedef)|[wsregex_token_iterator Typedef](#wsregex_token_iterator_typedef)|[wssub_match Typedef](#wssub_match_typedef)|  
  
##  <a name="a-namecmatchtypedefa--cmatch-typedef"></a><a name="cmatch_typedef"></a>  cmatch Typedef  
 char match_results 的類型定義。  
  
```  
typedef match_results<const char*> cmatch;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const char*` 類型迭代器的範本類別 [match_results 類別](../standard-library/match-results-class.md)的特製化。  
  
##  <a name="a-namecregexiteratortypedefa--cregexiterator-typedef"></a><a name="cregex_iterator_typedef"></a>  cregex_iterator Typedef  
 char regex_iterator 的類型定義。  
  
```  
typedef regex_iterator<const char*> cregex_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const char*` 類型迭代器之範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。  
  
##  <a name="a-namecregextokeniteratortypedefa--cregextokeniterator-typedef"></a><a name="cregex_token_iterator_typedef"></a>  cregex_token_iterator Typedef  
 Char regex_token_iterator 的類型定義  
  
```  
typedef regex_token_iterator<const char*> cregex_token_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const char*` 類型迭代器之範本類別 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。  
  
##  <a name="a-namecsubmatchtypedefa--csubmatch-typedef"></a><a name="csub_match_typedef"></a>  csub_match Typedef  
 char sub_match 的類型定義。  
  
```  
typedef sub_match<const char*> csub_match;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const char*` 類型迭代器之範本類別 [sub_match 類別](../standard-library/sub-match-class.md)的特製化。  
  
##  <a name="a-nameregextypedefa--regex-typedef"></a><a name="regex_typedef"></a>  regex Typedef  
 char basic_regex 的類型定義。  
  
```  
typedef basic_regex<char> regex;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `char` 類型項目之範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)的特製化。  
  
> [!NOTE]
>  高位元字元搭配 `regex` 將會有未預期的結果。 超出 0 到 127 範圍以外的值可能會導致未定義的行為。  
  
##  <a name="a-namesmatchtypedefa--smatch-typedef"></a><a name="smatch_typedef"></a>  smatch Typedef  
 string match_results 的類型定義。  
  
```  
typedef match_results<string::const_iterator> smatch;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `string::const_iterator` 類型迭代器的範本類別 [match_results 類別](../standard-library/match-results-class.md)的特製化。  
  
##  <a name="a-namesregexiteratortypedefa--sregexiterator-typedef"></a><a name="sregex_iterator_typedef"></a>  sregex_iterator Typedef  
 string regex_iterator 的類型定義。  
  
```  
typedef regex_iterator<string::const_iterator> sregex_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `string::const_iterator` 類型迭代器之範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。  
  
##  <a name="a-namesregextokeniteratortypedefa--sregextokeniterator-typedef"></a><a name="sregex_token_iterator_typedef"></a>  sregex_token_iterator Typedef  
 string regex_token_iterator 的類型定義。  
  
```  
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `string::const_iterator` 類型迭代器之範本類別 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。  
  
##  <a name="a-namessubmatchtypedefa--ssubmatch-typedef"></a><a name="ssub_match_typedef"></a>  ssub_match Typedef  
 string sub_match 的類型定義。  
  
```  
typedef sub_match<string::const_iterator> ssub_match;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `string::const_iterator` 類型迭代器之範本類別 [sub_match 類別](../standard-library/sub-match-class.md)的特製化。  
  
##  <a name="a-namewcmatchtypedefa--wcmatch-typedef"></a><a name="wcmatch_typedef"></a>  wcmatch Typedef  
 wchar_t match_results 的類型定義。  
  
```  
typedef match_results<const wchar_t *> wcmatch;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const wchar_t*` 類型迭代器的範本類別 [match_results 類別](../standard-library/match-results-class.md)的特製化。  
  
##  <a name="a-namewcregexiteratortypedefa--wcregexiterator-typedef"></a><a name="wcregex_iterator_typedef"></a>  wcregex_iterator Typedef  
 wchar_t regex_iterator 的類型定義。  
  
```  
typedef regex_iterator<const wchar_t*> wcregex_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const wchar_t*` 類型迭代器之範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。  
  
##  <a name="a-namewcregextokeniteratortypedefa--wcregextokeniterator-typedef"></a><a name="wcregex_token_iterator_typedef"></a>  wcregex_token_iterator Typedef  
 wchar_t regex_token_iterator 的類型定義。  
  
```  
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const wchar_t*` 類型迭代器之範本類別 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。  
  
##  <a name="a-namewcsubmatchtypedefa--wcsubmatch-typedef"></a><a name="wcsub_match_typedef"></a>  wcsub_match Typedef  
 wchar_t sub_match 的類型定義。  
  
```  
typedef sub_match<const wchar_t*> wcsub_match;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `const wchar_t*` 類型迭代器之範本類別 [sub_match 類別](../standard-library/sub-match-class.md)的特製化。  
  
##  <a name="a-namewregextypedefa--wregex-typedef"></a><a name="wregex_typedef"></a>  wregex Typedef  
 wchar_t basic_regex 的類型定義。  
  
```  
typedef basic_regex<wchar_t> wregex;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `wchar_t` 類型項目之範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)的特製化。  
  
##  <a name="a-namewsmatchtypedefa--wsmatch-typedef"></a><a name="wsmatch_typedef"></a>  wsmatch Typedef  
 wstring match_results 的類型定義。  
  
```  
typedef match_results<wstring::const_iterator> wsmatch;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `wstring::const_iterator` 類型迭代器的範本類別 [match_results 類別](../standard-library/match-results-class.md)的特製化。  
  
##  <a name="a-namewsregexiteratortypedefa--wsregexiterator-typedef"></a><a name="wsregex_iterator_typedef"></a>  wsregex_iterator Typedef  
 wstring regex_iterator 的類型定義。  
  
```  
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `wstring::const_iterator` 類型迭代器之範本類別 [regex_iterator 類別](../standard-library/regex-iterator-class.md)的特製化。  
  
##  <a name="a-namewsregextokeniteratortypedefa--wsregextokeniterator-typedef"></a><a name="wsregex_token_iterator_typedef"></a>  wsregex_token_iterator Typedef  
 wstring regex_token_iterator 的類型定義。  
  
```  
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `wstring::const_iterator` 類型迭代器之範本類別 [regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)的特製化。  
  
##  <a name="a-namewssubmatchtypedefa--wssubmatch-typedef"></a><a name="wssub_match_typedef"></a>  wssub_match Typedef  
 wstring sub_match 的類型定義。  
  
```  
typedef sub_match<wstring::const_iterator> wssub_match;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 `wstring::const_iterator` 類型迭代器之範本類別 [sub_match 類別](../standard-library/sub-match-class.md)的特製化。  
  
## <a name="see-also"></a>另請參閱  
[\<regex>](../standard-library/regex.md)  
[regex_constants 類別](../standard-library/regex-constants-class.md)  
[regex_error 類別](../standard-library/regex-error-class.md)  
[\<regex> 函式](../standard-library/regex-functions.md)  
[regex_iterator 類別](../standard-library/regex-iterator-class.md)  
[\<regex> 運算子](../standard-library/regex-operators.md)  
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)  
[regex_traits 類別](../standard-library/regex-traits-class.md)  

