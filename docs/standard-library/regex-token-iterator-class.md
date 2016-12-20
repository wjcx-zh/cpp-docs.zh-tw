---
title: "regex_token_iterator 類別 | Microsoft Docs"
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
  - "regex_token_iterator"
  - "std.tr1.regex_token_iterator"
  - "std::tr1::regex_token_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_token_iterator 類別 [TR1]"
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 15
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_token_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

子相符項目的迭代器類別。  
  
## 語法  
  
```  
template<class BidIt, class Elem = iterator_traits<BidIt>::value_type,  
    class RXtraits = regex_traits<Elem> >  
        class regex_token_iterator {  
public:  
    typedef basic_regex<Elem, RXtraits> regex_type;  
    typedef sub_match<BidIt> value_type;  
    typedef std::forward_iterator_tag iterator_category;  
    typedef std::ptrdiff_t difference_type;  
    typedef const sub_match<BidIt> *pointer;  
    typedef const sub_match<BidIt>& reference;  
  
    regex_token_iterator();  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, int submatch = 0,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const std::vector<int> submatches,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    template<std::size_t N>  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const int (&submatches)[N],  
        regex_constants::match_flag_type f = regex_constants::match_default);  
  
    bool operator==(const regex_token_iterator& right);  
    bool operator!=(const regex_token_iterator& right);  
    const basic_string<Elem>& operator*();  
    const basic_string<Elem> *operator->();  
    regex_token_iterator& operator++();  
    regex_token_iterator& operator++(int);  
private:  
    regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
    vector<int> subs;                         // exposition only  
    int pos;                                  // exposition only  
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
 此範本類別描述常數正向迭代器物件。 就概念而言，它會保存 `regex_iterator` 物件，以用來搜尋字元序列中的規則運算式相符項目。 它會擷取 `sub_match<BidIt>` 類型的物件，該物件代表針對每個規則運算式相符項目儲存的向量 `subs` 中的索引值所識別的子相符項目。  
  
 索引值 \-1 指定字元序列會在上一個規則運算式相符項目的結尾之後立即開始，如果之前沒有任何規則運算式相符項目，則會從字元序列的開頭開始，並延伸到 \(但不包含\) 目前規則運算式相符項目的第一個字元，如果目前沒有相符項目，則延伸到字元序列的結尾。 其他任何索引值 `idx` 則指定 `it.match[idx]` 中所保留之擷取群組的內容。  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)   
 [regex\_iterator 類別](../standard-library/regex-iterator-class.md)