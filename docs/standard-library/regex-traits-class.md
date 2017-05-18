---
title: "regex_traits 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_traits
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
dev_langs:
- C++
helpviewer_keywords:
- regex_traits class
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: b7a7b0cfe5614cb87d82634e6d17643f5509ae13
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="regextraits-class"></a>regex_traits 類別
描述進行比對的元素特性。  
  
## <a name="syntax"></a>語法  
```  
template<class Elem>
class regex_traits {  
public:  
   typedef Elem char_type;  
   typedef size_t size_type;  
   typedef basic_string<Elem> string_type;  
   typedef locale locale_type;  
   typedef ctype_base::mask char_class_type;  

   regex_traits();
   static size_type length(const char_type *str);
   char_type translate(char_type ch) const;
   char_type translate_nocase(char_type ch) const;
   template <class FwdIt>  
   string_type transform(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   string_type transform_primary(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   char_class_type lookup_classname(FwdIt first, FwdIt last) const;
   template <class FwdIt>  
   string_type lookup_collatename(FwdIt first, FwdIt last) const;
   bool isctype(char_type ch, char_class_type cls) const;
   int value(char_type ch, int base) const;
   locale_type imbue(locale_type loc);
   locale_type getloc() const;
};  
 ``` 
#### <a name="parameters"></a>參數  
 `Elem`  
 要描述的字元項目類型。  
  
## <a name="remarks"></a>備註  
 範本類別會描述類型 `Elem`的各種規則運算式特性。 範本類別 [basic_regex 類別](../standard-library/basic-regex-class.md)會使用此資訊來管理 `Elem` 類型的項目。  
  
 每個 `regex_traits` 物件都擁有一個類型 `regex_traits::locale` 的物件，這種類型可為其部分成員函式使用。 預設的地區設定是 `regex_traits::locale()`的複本。 成員函式 `imbue` 取代了地區設定物件，而成員函式 `getloc` 會傳回地區設定物件的複本。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<regex>  
  
 **命名空間：** std  
  
##  <a name="char_class_type"></a>  regex_traits::char_class_type  
 字元類別指示項的類型。  
  
```  
typedef T8 char_class_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型是指定字元類別之未指定類型的同義字。 這個類型的值可以透過 `|` 運算子來結合，以指定做為運算元所指定之類別聯集的字元類別。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_char_class_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="char_type"></a>  regex_traits::char_type  
 元素的類型。  
  
```  
typedef Elem char_type;  
```  
  
### <a name="remarks"></a>備註  
 typedef 是範本引數 `Elem`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_char_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="getloc"></a>  regex_traits::getloc  
 傳回儲存的地區設定物件。  
  
```  
locale_type getloc() const;
```  
  
### <a name="remarks"></a>備註  
 成員函式會傳回儲存的 `locale` 物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_getloc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="imbue"></a>  regex_traits::imbue  
 修改儲存的地區設定物件。  
  
```  
locale_type imbue(locale_type loc);
```  
  
### <a name="parameters"></a>參數  
 `loc`  
 要儲存的地區設定物件。  
  
### <a name="remarks"></a>備註  
 成員函式會將 `loc` 複製到儲存的 `locale` 物件，並傳回已儲存 `locale` 物件之先前值的複本。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_imbue.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="isctype"></a>  regex_traits::isctype  
 測試是否有類別成員資格。  
  
```  
bool isctype(char_type ch, char_class_type cls) const;
```  
  
### <a name="parameters"></a>參數  
 `ch`  
 待測試的項目。  
  
 `cls`  
 做為測試對象的類別。  
  
### <a name="remarks"></a>備註  
 只有在字元 `ch` 位於 `cls`所指定的字元類別時，此成員函式才會傳回 true。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_isctype.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="length"></a>  regex_traits::length  
 傳回 nul-terminated 序列的長度。  
  
```  
static size_type length(const char_type *str);
```  
  
### <a name="parameters"></a>參數  
 `str`  
 nul-terminated 序列。  
  
### <a name="remarks"></a>備註  
 此靜態成員函式傳回 `std::char_traits<char_type>::length(str)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_length.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="locale_type"></a>  regex_traits::locale_type  
 儲存的地區設定物件類型。  
  
```  
typedef T7 locale_type;  
```  
  
### <a name="remarks"></a>備註  
 Typedef 是封裝地區設定之類型的同義字。 在特製化 `regex_traits<char>` 和 `regex_traits<wchar_t>` 時，此為 `std::locale`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_locale_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="lookup_classname"></a>  regex_traits::lookup_classname  
 將序列對應至字元類別。  
  
```  
template <class FwdIt>  
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要查閱之序列的開頭。  
  
 `last`  
 要查閱之序列的結尾。  
  
### <a name="remarks"></a>備註  
 成員函式會傳回一個值，指定由字元序列命名、依引數指向的字元類別。 此值不依存於序列中字元的大小寫。  
  
 特製化 `regex_traits<char>` 會辨識名稱 `"d"`、`"s"`、`"w"`、`"alnum"`、`"alpha"`、`"blank"`、`"cntrl"`、`"digit"`、`"graph"`、`"lower"`、`"print"`、`"punct"`、`"space"`、`"upper"` 和 `"xdigit"`，且完全不考量大小寫。  
  
 特製化 `regex_traits<wchar_t>` 會辨識名稱 `L"d"`、`L"s"`、`L"w"`、`L"alnum"`、`L"alpha"`、`L"blank"`、`L"cntrl"`、`L"digit"`、`L"graph"`、`L"lower"`、`L"print"`、`L"punct"`、`L"space"`、`L"upper"` 和 `L"xdigit"`，且完全不考量大小寫。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_lookup_classname.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="lookup_collatename"></a>  regex_traits::lookup_collatename  
 將序列對應至定序項目。  
  
```  
template <class FwdIt>  
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要查閱之序列的開頭。  
  
 `last`  
 要查閱之序列的結尾。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回含有對應至序列 `[first, last)`之定序項目的字串物件；如果序列不是有效的定序項目，則傳回空字串。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_lookup_collatename.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="regex_traits"></a>  regex_traits::regex_traits  
 建構物件。  
  
```  
regex_traits();
```  
  
### <a name="remarks"></a>備註  
 建構函式會建構已儲存的 `locale` 物件初始化為預設地區設定的物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="size_type"></a>  regex_traits::size_type  
 序列長度的類型。  
  
```  
typedef T6 size_type;  
```  
  
### <a name="remarks"></a>備註  
 此 typedef 是不帶正負號之整數類型的同義字。 在特製化 `regex_traits<char>` 和 `regex_traits<wchar_t>` 時，此為 `std::size_t` 的同義字。  
  
 此 typedef 是 `std::size_t` 的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_size_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="string_type"></a>  regex_traits::string_type  
 元素字串的類型。  
  
```  
typedef basic_string<Elem> string_type;  
```  
  
### <a name="remarks"></a>備註  
 此 typedef 是 `basic_string<Elem>`的同義字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_string_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="transform"></a>  regex_traits::transform  
 轉換成相等的已排序序列。  
  
```  
template <class FwdIt>  
string_type transform(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要轉換之序列的開頭。  
  
 `last`  
 要轉換之序列的結尾。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回根據儲存的 `locale` 物件，使用轉換規則所產生的字串。 至於迭代器範圍 `[first1, last1)` 和 `[first2, last2)`所指定的兩個字元序列，如果迭代器範圍 `transform(first1, last1) < transform(first2, last2)` 所指定的字元序列排在迭代器範圍 `[first1, last1)` 所指定的字元序列前面，則 `[first2, last2)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_transform.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="transform_primary"></a>  regex_traits::transform_primary  
 轉換成相等且不區分大小寫的已排序序列。  
  
```  
template <class FwdIt>  
string_type transform_primary(FwdIt first, FwdIt last) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要轉換之序列的開頭。  
  
 `last`  
 要轉換之序列的結尾。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回根據儲存的 `locale` 物件，使用轉換規則所產生的字串。 至於迭代器範圍 `[first1, last1)` 和 `[first2, last2)`所指定的兩個字元序列，如果迭代器範圍 `transform_primary(first1, last1) < transform_primary(first2, last2)` 所指定的字元序列排在迭代器範圍 `[first1, last1)` 所指定的字元序列前面，則 `[first2, last2)` ，而不必考慮大小寫或腔調字。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_transform_primary.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="translate"></a>  regex_traits::translate  
 轉換成相等的相符元素。  
  
```  
char_type translate(char_type ch) const;
```  
  
### <a name="parameters"></a>參數  
 `ch`  
 要轉換的項目。  
  
### <a name="remarks"></a>備註  
 使用取決於預存 `locale` 物件的轉換規則，成員函式會傳回它產生的字元。 至於兩個 `char_type` 物件 `ch1` 和 `ch2`，唯有 `translate(ch1) == translate(ch2)` 和 `ch1` 符合這個情況：一個發生在規則運算式定義，另一個發生在區分地區設定相符項目之目標序列的對應位置時，才會是 `ch2` 。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_translate.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="translate_nocase"></a>  regex_traits::translate_nocase  
 轉換成相等且不區分大小寫的相符項目。  
  
```  
char_type translate_nocase(char_type ch) const;
```  
  
### <a name="parameters"></a>參數  
 `ch`  
 要轉換的項目。  
  
### <a name="remarks"></a>備註  
 使用取決於預存 `locale` 物件的轉換規則，成員函式會傳回它產生的字元。 至於兩個 `char_type` 物件 `ch1` 和 `ch2`，唯有 `translate_nocase(ch1) == translate_nocase(ch2)` 和 `ch1` 符合這個情況：一個發生在規則運算式定義，另一個發生在區分大小寫相符項目之目標序列的對應位置時，才會是 `ch2` 。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_translate_nocase.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
##  <a name="value"></a>  regex_traits::value  
 將項目轉換成數值。  
  
```  
int value(Elem ch, int radix) const;
```  
  
### <a name="parameters"></a>參數  
 `ch`  
 要轉換的項目。  
  
 `radix`  
 要使用的算術基底。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回以基底 `ch` 中字元 `radix`表示的值；如果 `ch` 不是基底 `radix`中的有效數字，則傳回 -1。 此函式只會透過 8，10 或 16 的 `radix` 引數進行呼叫。  
  
### <a name="example"></a>範例  
  
```cpp  
// std__regex__regex_traits_value.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_traits<char> Mytr;   
int main()   
    {   
    Mytr tr;   
  
    Mytr::char_type ch = tr.translate('a');   
    std::cout << "translate('a') == 'a' == " << std::boolalpha   
        << (ch == 'a') << std::endl;   
  
    std::cout << "nocase 'a' == 'A' == " << std::boolalpha   
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))   
        << std::endl;   
  
    const char *lbegin = "abc";   
    const char *lend = lbegin + strlen(lbegin);   
    Mytr::size_type size = tr.length(lbegin);   
    std::cout << "length(\"abc\") == " << size <<std::endl;   
  
    Mytr::string_type str = tr.transform(lbegin, lend);   
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha   
        << (str < "abc") << std::endl;   
  
    const char *ubegin = "ABC";   
    const char *uend = ubegin + strlen(ubegin);   
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha   
        << (tr.transform_primary(ubegin, uend) <   
            tr.transform_primary(lbegin, lend))   
        << std::endl;   
  
    const char *dig = "digit";   
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);   
    std::cout << "class digit == d == " << std::boolalpha   
        << (cl == tr.lookup_classname(dig, dig + 1))   
        << std::endl;   
  
    std::cout << "'3' is digit == " <<std::boolalpha   
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))   
        << std::endl;   
  
    std::cout << "hex C == " << tr.value('C', 16) << std::endl;   
  
// other members   
    str = tr.lookup_collatename(dig, dig + 5);   
  
    Mytr::locale_type loc = tr.getloc();   
    tr.imbue(loc);   
  
    return (0);   
    }  
  
```  
  
```Output  
translate('a') == 'a' == true  
nocase 'a' == 'A' == true  
length("abc") == 3  
transform("abc") < "abc" == false  
primary "ABC" < "abc" == false  
class digit == d == true  
'3' is digit == true  
hex C == 12  
```  
  
## <a name="see-also"></a>另請參閱  
[\<regex>](../standard-library/regex.md)  
[regex_constants 類別](../standard-library/regex-constants-class.md)  
[regex_error 類別](../standard-library/regex-error-class.md)  
[\<regex> 函式](../standard-library/regex-functions.md)  
[regex_iterator 類別](../standard-library/regex-iterator-class.md)  
[\<regex> 運算子](../standard-library/regex-operators.md)  
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  
 [regex_traits\<char> 類別](../standard-library/regex-traits-char-class.md)   
 [regex_traits\<wchar_t> 類別](../standard-library/regex-traits-wchar-t-class.md)


