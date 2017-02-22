---
title: "array 類別 (STL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "array/std::tr1::array"
  - "std.tr1.array"
  - "array"
  - "std::tr1::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array 類別 [TR1]"
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# array 類別 (STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明的物件可控制長度 `N` 之 `Ty` 類型項目的序列。  序列會儲存成陣列 `Ty`，包含在 `array<Ty, N>` 物件中。  
  
## 語法  
  
```  
template<class Ty, std::size_t N>  
    class array;  
```  
  
#### 參數  
  
|||  
|-|-|  
|參數|描述|  
|`Ty`|項目的類型。|  
|`N`|元素數。|  
  
## Members  
  
|||  
|-|-|  
|類型定義|描述|  
|[array::const\_iterator](../Topic/array::const_iterator.md)|用於受控制序列的常數迭代器類型。|  
|[array::const\_pointer](../Topic/array::const_pointer.md)|項目的常數指標類型。|  
|[array::const\_reference](../Topic/array::const_reference.md)|項目的常數參考類型。|  
|[array::const\_reverse\_iterator](../Topic/array::const_reverse_iterator.md)|用於受控制序列的常數反向迭代器類型。|  
|[array::difference\_type](../Topic/array::difference_type.md)|兩個項目之間的帶正負號距離的類型。|  
|[array::iterator](../Topic/array::iterator.md)|受控制序列之迭代器的類型。|  
|[array::pointer](../Topic/array::pointer.md)|項目的指標類型。|  
|[array::reference](../Topic/array::reference.md)|項目的參考類型。|  
|[array::reverse\_iterator](../Topic/array::reverse_iterator.md)|受控制序列的反向迭代器類型。|  
|[array::size\_type](../Topic/array::size_type.md)|兩個項目之間的不帶正負號距離的類型。|  
|[array::value\_type](../Topic/array::value_type.md)|項目的類型。|  
  
|||  
|-|-|  
|成員函式|描述|  
|[array::array](../Topic/array::array.md)|建構陣列物件。|  
|[array::assign](../Topic/array::assign.md)|取代所有項目。|  
|[array::at](../Topic/array::at.md)|存取指定位置的項目。|  
|[array::back](../Topic/array::back.md)|存取最後一個項目。|  
|[array::begin](../Topic/array::begin.md)|指定受控制序列的開頭。|  
|[array::cbegin](../Topic/array::cbegin.md)|將隨機存取常數迭代器傳回陣列中的第一個項目。|  
|[array::cend](../Topic/array::cend.md)|傳回隨機存取指向陣列結尾之後一個項目的常數迭代器。|  
|[array::crbegin](../Topic/array::crbegin.md)|將常數迭代器傳回反向陣列中的第一個項目。|  
|[array::crend](../Topic/array::crend.md)|將常數迭代器傳回反向陣列的結尾。|  
|[array::data](../Topic/array::data.md)|取得第一個項目的位址。|  
|[array::empty](../Topic/array::empty.md)|測試項目是否存在。|  
|[array::end](../Topic/array::end.md)|指定受控制序列的結尾。|  
|[array::fill](../Topic/array::fill.md)|取代所有具有指定值的項目。|  
|[array::front](../Topic/array::front.md)|存取第一個項目。|  
|[array::max\_size](../Topic/array::max_size.md)|計算項目的數目。|  
|[array::rbegin](../Topic/array::rbegin.md)|指定反向受控制序列的開頭。|  
|[array::rend](../Topic/array::rend.md)|指定反向受控制序列的結尾。|  
|[array::size](../Topic/array::size.md)|計算項目的數目。|  
|[array::swap](../Topic/array::swap.md)|交換兩個容器的內容。|  
  
|||  
|-|-|  
|運算子|描述|  
|[array::operator\=](../Topic/array::operator=.md)|取代受控制的序列。|  
|[array::operator](../Topic/array::operator.md)|存取指定位置的項目。|  
  
## 備註  
 該類型具有預設建構函式 `array()` 與預設指派運算子 `operator=`，且可滿足 `aggregate` 的需求。  因此，`array<Ty, N>` 類型的物件可以使用彙總初始設定式加以初始化。  例如：  
  
```  
array<int, 4> ai = { 1, 2, 3 };  
```  
  
 建立含有四個整數值的物件 `ai`，將前三個項目分別初始化為值 1、 2 和 3，並將第四個項目初始化為 0。  
  
## 需求  
 **標頭：**\<array\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<array\>](../standard-library/array.md)