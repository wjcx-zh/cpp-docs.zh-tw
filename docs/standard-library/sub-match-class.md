---
title: "sub_match 類別 | Microsoft Docs"
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
  - "sub_match"
  - "std::tr1::sub_match"
  - "std.tr1.sub_match"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sub_match 類別 [TR1]"
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sub_match 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述子相符項目。  
  
## 語法  
  
```  
template<class BidIt>  
    class sub_match  
        : public std::pair<BidIt, BidIt> {  
public:  
    bool matched;  
    int compare(const sub_match& right) const;  
    int compare(const basic_string<value_type>& right) const;  
    int compare(const value_type *right) const;  
    difference_type length() const;  
    operator basic_string<value_type>() const;  
    basic_string<value_type> str() const;  
    typedef typename iterator_traits<BidIt>::value_type value_type;  
    typedef typename iterator_traits<BidIt>::difference_type difference_type;  
    typedef BidIt iterator;  
    };  
```  
  
#### 參數  
 `BidIt`  
 子相符項目的迭代器類型。  
  
## 備註  
 此範本類別所描述的物件，會指定與 [regex\_match 函式](../Topic/regex_match%20Function.md) 或 [regex\_search 函式](../Topic/regex_search%20Function.md) 呼叫中的擷取群組相符的字元序列。[match\_results 類別](../standard-library/match-results-class.md) 類型的物件會保存這些物件的陣列，每個陣列分別代表用於搜尋之規則運算式中的一個擷取群組。  
  
 如果擷取群組與物件的資料成員不符，則 `matched` 為 false，且兩個迭代器 `first` 和 `second` \(繼承自基底 `std::pair`\) 相等。 如果擷取群組相符，則 `matched` 為 true，迭代器 `first` 會指向目標序列中符合擷取群組的第一個字元，而 `second` 會指向目標序列中符合擷取群組之最後一個字元後的一個位置。 請注意，如果零長度與成員相符，則 `matched` 為零，且兩個迭代器相等，並且都會指向相符項目的位置。  
  
 當擷取群組只包含一個判斷提示，或包含一個允許重複零的重複項目時，可能會發生零長度相符的情況。 例如：  
  
 "^" 與目標序列 "a" 相符；對應至擷取群組 0 的 `sub_match` 物件會保存同時指向序列中第一個字元的兩個迭代器。  
  
 "b\(a\*\)b" 與目標序列 "bb" 相符；對應至擷取群組 1 的 `sub_match` 物件會保存同時指向序列中第二個字元的兩個迭代器。  
  
## 需求  
 **標頭：**\<regex\>  
  
 **命名空間：**std  
  
## 請參閱  
 [\<regex\>](../standard-library/regex.md)   
 [sub\_match](../standard-library/sub-match-class.md)   
 [regex\_match 函式](../Topic/regex_match%20Function.md)   
 [regex\_search 函式](../Topic/regex_search%20Function.md)