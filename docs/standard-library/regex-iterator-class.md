---
title: "regex_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::regex_iterator"
  - "std.tr1.regex_iterator"
  - "regex_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_iterator 類別 [TR1]"
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# regex_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

相符項目的迭代器類別。  
  
## 語法  
  
```  
template<class BidIt, class Elem = iterator_traits<BidIt>::value_type,  
    class RXtraits = regex_traits<Elem> >  
        class regex_iterator {  
public:  
    typedef basic_regex<Elem, RXtraits> regex_type;  
    typedef match_results<BidIt> value_type;  
    typedef std::forward_iterator_tag iterator_category;  
    typedef std::ptrdiff_t difference_type;  
    typedef const match_results<BidIt>* pointer;  
    typedef const match_results<BidIt>& reference;  
  
    regex_iterator();  
    regex_iterator(BidIt first, BidIt last,  
        const regex_type& re,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
  
    bool operator==(const regex_iterator& right);  
    bool operator!=(const regex_iterator& right);  
    const match_results<BidIt>& operator*();  
    const match_results<BidIt> *operator->();  
    regex_iterator& operator++();  
    regex_iterator& operator++(int);  
  
    BidIt begin;                            // exposition only  
    BidIt end;                              // exposition only  
    regex_type *pregex;                     // exposition only  
    regex_constants::match_flag_type flags; // exposition only  
    match_results<BidIt> match;             // exposition only  
    };  
```  
  
#### 參數  
 `BidIt`  
 子相符項目的迭代器類型。  
  
 `Elem`  
 要符合之項目的類型。  
  
 `RXtraits`  
 項目的 Traits 類別。  
  
## 備註  
 此樣板類別描述常數正向迭代器物件。 它會將其規則運算式物件 `*pregex` 重複套用至迭代器範圍 `[begin, end)` 所定義的字元序列，藉以擷取 `match_results<BidIt>` 類型的物件。  
  
## 範例  
 如需規則運算式的相關範例，請參閱下列主題：  
  
-   [regex\_match 函式](../Topic/regex_match%20Function.md)  
  
-   [regex\_replace 函式](../Topic/regex_replace%20Function.md)  
  
-   [regex\_search 函式](../Topic/regex_search%20Function.md)  
  
-   [swap 函式](../Topic/swap%20Function%20%3Cregex%3E.md)  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_iterator](../standard-library/regex-iterator-class.md)