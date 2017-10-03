---
title: '&lt;string&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
caps.latest.revision: 12
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 683d3f5848ab86a9a80c25a09ac110b2abb2f5e2
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltstringgt-typedefs"></a>&lt;string&gt; typedef
||||  
|-|-|-|  
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|  
|[wstring](#wstring)|  
  
##  <a name="string"></a>  string  
 類型，描述使用 `char` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。  
  
 其他特製化 `basic_string` 的 typedef 包含 [wstring](../standard-library/string-typedefs.md#wstring)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。  
  
```cpp  
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```  
  
### <a name="remarks"></a>備註  
 以下宣告是相同的：  
  
```cpp  
string str("");

basic_string<char> str("");
```  
  
 如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。  
  
##  <a name="u16string"></a>  u16string  
 類型，描述使用 `char16_t` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。  
  
 其他特製化 `basic_string` 的 typedef 包含 [wstring](../standard-library/string-typedefs.md#wstring)、[string](../standard-library/string-typedefs.md#string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。  
  
```cpp  
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```  
  
### <a name="remarks"></a>備註  
 如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。  
  
##  <a name="u32string"></a>  u32string  
 類型，描述使用 `char32_t` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。  
  
 其他特製化 `basic_string` 的 typedef 包含 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [wstring](../standard-library/string-typedefs.md#wstring)。  
  
```cpp  
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```  
  
### <a name="remarks"></a>備註  
 如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。  
  
##  <a name="wstring"></a>  wstring  
 類型，描述使用 `wchar_t` 類型的項目特製化樣板類別 [basic_string](../standard-library/basic-string-class.md)。  
  
 其他特製化 `basic_string` 的 typedef 包含 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 及 [u32string](../standard-library/string-typedefs.md#u32string)。  
  
```cpp  
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```  
  
### <a name="remarks"></a>備註  
 以下宣告是相同的：  
  
```cpp  
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```  
  
 如需 string 建構函式的清單，請參閱 [basic_string:: basic_string](../standard-library/basic-string-class.md#basic_string)。  
  
> [!NOTE]
>  `wchar_t` 的大小是由實作定義。 如果您的程式碼取決於 `wchar_t` 的特定大小，請檢查您的平台實作 (例如，使用 `sizeof(wchar_t)`)。 如果您需要的字串字元類型保證會在所有平台上具有相同寬度，請使用 [string](../standard-library/string-typedefs.md#string)、[u16string](../standard-library/string-typedefs.md#u16string) 或 [u32string](../standard-library/string-typedefs.md#u32string)。  
  
## <a name="see-also"></a>另請參閱  
 [\<string>](../standard-library/string.md)




