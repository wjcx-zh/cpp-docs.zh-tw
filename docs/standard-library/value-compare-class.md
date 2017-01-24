---
title: "類別 value_compare 類別 | Microsoft Docs"
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
  - "value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare 類別"
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 類別 value_compare 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供可以藉由比較其索引鍵的值會決定它們在 hash\_map 的相對順序比較 hash\_map 元素的函式物件。  
  
## 語法  
  
```  
class value_compare  
    : std::public binary_function<value_type, value_type, bool>   
{  
public:  
    bool operator( )(  
        const value_type& _Left,  
        const value_type& _Right ) const  
        {  
            return ( comp( _Left.first, _Right.first ) );   
        }  
protected:  
    value_compare( const key_compare& c ) : comp (c) { }  
    key_compare comp;  
};  
```  
  
## 備註  
 在整個項目包含之間 **value\_types** 的 value\_compare 提供的比較準則 hash\_map 中個別項目的索引鍵之間的比較產生的結構描述類別建構。  成員函式會使用物件在函式物件儲存的型別 `key_compare`**comp** 提供 value\_compare 比較兩個項目排序索引鍵元件。  
  
 如需 hash\_sets 和 hash\_multisets，是簡單的容器索引鍵值與項目值相同， value\_compare 相當於 `key_compare`;如需 hash\_maps 和 hash\_multimaps 它們不是，，因為型別 `pair` 項目的值與項目的索引鍵的值不相同。  
  
 在 Visual C\+\+ .NET 2003 中， [\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 標頭檔的成員不在 std 命名空間中，而是移至 stdext 命名空間。  如需詳細資訊，請參閱 [stdext 命名空間](../standard-library/stdext-namespace.md)。  
  
## 範例  
 中的 [hash\_map::value\_comp](../Topic/hash_map::value_comp.md) 參閱本範例說明如何宣告和使用 value\_compare。  
  
## 需求  
 **標頭檔:** \<hash\_map\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [binary\_function 結構](../standard-library/binary-function-struct.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)