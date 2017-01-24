---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference 函式"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
相同 [adjacent\_difference](../Topic/adjacent_difference.md), ，允許使用未檢查迭代器做為輸出迭代器，但當 \_SECURE\_SCL \= 1 會定義。`unchecked_adjacent_difference` 定義於 `stdext` 命名空間。  
  
> [!NOTE]
>  這個演算法是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。 使用這個演算法實作的程式碼不可移植。  
  
## 語法  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### 參數  
 `_First`  
 輸入迭代器，為輸入範圍中的第一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。  
  
 `_Last`  
 輸入迭代器，為輸入範圍中的最後一個項目定址，該範圍中的項目與其各自的前置項要有差異，或一對值要由另一個指定的二進位運算作業。  
  
 `_Result`  
 輸出迭代器，定址在目的範圍中的第一個項目，該範圍中要存放一系列差異或指定作業的結果。  
  
 `_Binary_op`  
 要套用在一般化作業中的二進位運算，取代差異程序的減法運算。  
  
## 傳回值  
 輸出迭代器定址目的範圍結尾︰ `_Result` \+ \(`_Last` \- `_First`\)。  
  
## 備註  
 請參閱 [adjacent\_difference](../Topic/adjacent_difference.md) 程式碼範例。  
  
 如需已檢查的迭代器的詳細資訊，請參閱 [已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
## 需求  
 **標頭：**\<numeric\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [標準樣板程式庫](../misc/standard-template-library.md)