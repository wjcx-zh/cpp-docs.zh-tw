---
title: "basic_regex 類別 | Microsoft Docs"
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
  - "std::tr1::basic_regex"
  - "basic_regex"
  - "std.tr1.basic_regex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_regex 類別 [TR1]"
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
caps.latest.revision: 21
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# basic_regex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝規則運算式。  
  
## 語法  
  
```  
template<class Elem,  
    class RXtraits = regex_traits<Elem>,  
    class basic_regex {  
public:  
    basic_regex();  
    explicit basic_regex(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    basic_regex(const basic_regex& right);  
    template<class STtraits, class STalloc>  
        explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,  
            flag_type flags = ECMAScript);  
    template<class InIt>  
        explicit basic_regex(InIt first, InIt last,  
            flag_type flags = ECMAScript);  
  
    basic_regex& operator=(const basic_regex& right);  
    basic_regex& operator=(const Elem *ptr);  
    template<class STtraits, class STalloc>  
        basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);  
    basic_regex& assign(const basic_regex& right);  
    basic_regex& assign(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex& assign(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    template<class STtraits, class STalloc>  
    basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,  
        flag_type flags = ECMAScript);  
    template<class InIt>  
        basic_regex& assign(InIt first, InIt last,  
            flag_type flags = ECMAScript);  
  
    locale_type imbue(locale_type loc);  
    locale_type getloc() const;  
    void swap(basic_regex& other) throw();  
    unsigned mark_count() const;  
    flag_type flags() const;  
  
    typedef Elem value_type;  
    typedef regex_constants::syntax_option_type flag_type;  
    typedef typename RXtraits::locale_type locale_type;  
    static const flag_type icase = regex_constants::icase;  
    static const flag_type nosubs = regex_constants::nosubs;  
    static const flag_type optimize = regex_constants::optimize;  
    static const flag_type collate = regex_constants::collate;  
    static const flag_type ECMAScript = regex_constants::ECMAScript;  
    static const flag_type basic = regex_constants::basic;  
    static const flag_type extended = regex_constants::extended;  
    static const flag_type awk = regex_constants::awk;  
    static const flag_type grep = regex_constants::grep;  
    static const flag_type egrep = regex_constants::egrep;  
private:  
    RXtraits traits;    // exposition only  
    };  
```  
  
#### 參數  
 `Elem`  
 要符合之項目的類型。  
  
 `RXtraits`  
 項目的 Traits 類別。  
  
## 備註  
 此樣板類別描述保存規則運算式的物件。  這個樣板類別的物件可以傳遞至樣板函式 [regex\_match 函式](../Topic/regex_match%20Function.md)、[regex\_search 函式](../Topic/regex_search%20Function.md) 和 [regex\_replace 函式](../Topic/regex_replace%20Function.md) \(以及適當的文字字串引數\)，以搜尋符合規則運算式的文字。  這個樣板類別有兩個特製化：類型定義 [regex Typedef](../Topic/regex%20Typedef.md) 適用於 `char` 類型項目，[wregex Typedef](../Topic/wregex%20Typedef.md) 適用於 `wchar_t` 類型項目。  
  
 樣板引數 `RXtraits` 描述此樣板類別支援之規則運算式語法的各種重要屬性。  指定這些規則運算式特性的類別必須具有和 [regex\_traits 類別](../standard-library/regex-traits-class.md) 樣板類別物件相同的外部介面。  
  
 有些函式會接受定義規則運算式的運算元序列。  您可以透過數種方法指定這類運算元序列：  
  
 `ptr` \-\- 以 null 終止的序列 \(例如 C 字串，用於 `Elem` 類型的 `char`\)，開始位置在 `ptr` \(這不可以是 null 指標\)，其中終端項目為 `value_type()` 值，而且不是運算元序列的一部分  
  
 `ptr`, `count` \-\- `count` 項目序列，開始位置在 `ptr` \(這不可以是 null 指標\)  
  
 `str` \-\- `basic_string` 物件 `str` 所指定的序列  
  
 `first`, `last` \-\- 由範圍 `first` 中的迭代器 `last` 與 `[first, last)` 分隔的項目序列  
  
 `right` \-\- `basic_regex` 物件 `right`  
  
 除了 `flags` 類型描述的以外，這些成員函式也接受引數 `RXtraits`，為規則運算式解譯指定各種選項。  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_match 函式](../Topic/regex_match%20Function.md)   
 [regex\_search 函式](../Topic/regex_search%20Function.md)   
 [regex\_replace 函式](../Topic/regex_replace%20Function.md)   
 [regex Typedef](../Topic/regex%20Typedef.md)   
 [wregex Typedef](../Topic/wregex%20Typedef.md)   
 [regex\_traits 類別](../standard-library/regex-traits-class.md)