---
title: "value_compare 類別 (&lt;map&gt;) | Microsoft Docs"
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
  - "std::value_compare"
  - "std.value_compare"
  - "map/std::value_compare"
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 類別"
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# value_compare 類別 (&lt;map&gt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供可以藉由比較其索引鍵的值會決定其對應中的相對順序比較對應的項目的函式物件。  
  
## 語法  
  
```  
class value_compare : public binary_function<value_type, value_type, bool>  
{  
public:  
   bool operator()(const value_type& _Left, const value_type& _Right) const;  
   value_compare(key_compare _Pred) : comp(_Pred);  
   protected:  
      key_compare comp;  
};  
```  
  
## 備註  
 在整個項目包含之間 **value\_types** 的 `value_compare` 所提供的比較準則對應中的個別項目的索引鍵之間的比較產生的結構描述類別建構。  成員函式會使用物件在函式物件儲存的型別 `key_compare`**comp** 所提供的 `value_compare` 來比較兩個項目排序索引鍵元件。  
  
 針對集合和多重集，是簡單的容器索引鍵值與項目值相同時， `value_compare` 相當於 `key_compare`;如需對應和多重對應它們不是，，因為型別 `pair` 項目的值與項目的索引鍵的值不相同。  
  
## 範例  
 中的 [value\_comp](../Topic/map::value_comp.md) 參閱示範如何宣告和使用 `value_compare`。  
  
## 需求  
 **標頭：**\<map\>  
  
 **命名空間:** std  
  
## 請參閱  
 [binary\_function 結構](../standard-library/binary-function-struct.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)