---
title: "regex_traits 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "regex_traits"
  - "std::tr1::regex_traits"
  - "std.tr1.regex_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_traits 類別 [TR1]"
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_traits 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述進行比對的元素特性。  
  
## 語法  
  
```  
template<class Elem>  
    struct regex_traits {  
    regex_traits();  
  
    static size_type length(const char_type *str);  
    char_type translate(char_type ch) const;  
    char_type translate_nocase(char_type ch) const;  
    template<class FwdIt>  
        string_type transform(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type transform_primary(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        char_class_type lookup_classname(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type lookup_collatename(FwdIt first, FwdIt last) const;  
    bool isctype(char_type ch, char_class_type cls) const;  
    int value(Elem ch, int base) const;  
    locale_type imbue(locale_type loc);  
    locale_type getloc() const;  
  
    typedef Elem char_type;  
    typedef T6 size_type;  
    typedef basic_string<Elem> string_type;  
    typedef T7 locale_type;  
    typedef T8 char_class_type;  
    };  
```  
  
#### 參數  
 `Elem`  
 要描述的元素類型。  
  
## 備註  
 範本類別會描述類型 `Elem` 的各種規則運算式特性。 範本類別 [basic\_regex 類別](../standard-library/basic-regex-class.md) 使用這項資訊來操控類型 `Elem` 的元素。  
  
 每個 `regex_traits` 物件都擁有一個類型 `regex_traits::locale` 的物件，這種類型可為其部分成員函式使用。 預設的地區設定是 `regex_traits::locale()` 的複本。 成員函式 `imbue` 取代了地區設定物件，而成員函式 `getloc` 會傳回地區設定物件的複本。  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_traits](../standard-library/regex-traits-class.md)   
 [regex\_traits \< char \> 類別](../standard-library/regex-traits-char-class.md)   
 [regex\_traits\<wchar\_t\> 類別](../standard-library/regex-traits-wchar-t-class.md)