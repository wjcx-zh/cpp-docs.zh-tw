---
title: "hash 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.hash"
  - "xfunctional/std::hash"
  - "hash"
  - "typeindex/std::hash"
  - "std::hash"
  - "std.tr1.hash"
  - "std::tr1::hash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash 類別"
  - "hash 類別 [TR1]"
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# hash 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

計算值的雜湊程式碼。  
  
## 語法  
  
```  
template<class Ty>  
    struct hash  
        : public unary_function<Ty, size_t> {  
    size_t operator()(Ty _Val) const;  
    };  
```  
  
## 備註  
 成員函式定義雜湊函式，適合於對應型別 `Ty` 的值為索引值的散發。  成員運算子會傳回 `_Val`的雜湊程式碼，適合使用樣板類別 `unordered_map`、 `unordered_multimap`、 `unordered_set`和 `unordered_multiset`的。  `Ty` 可以是任何純量型別、 `string`、 `wstring`、 `error_code`、 `error_condition`、 `u16string`或 `u32string`。  
  
## 範例  
  
```  
// std_tr1__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
 **3**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<unordered\_map\>](../standard-library/unordered-map.md)   
 [unordered\_multimap 類別](../standard-library/unordered-multimap-class.md)   
 [unordered\_multiset 類別](../standard-library/unordered-multiset-class.md)   
 [\<unordered\_set\>](../standard-library/unordered-set.md)