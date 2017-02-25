---
title: "unorm_2 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator+="
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::y"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::set_y"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::x"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator--"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator*="
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::xy"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::get_y"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator="
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::set_x"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::rg"
  - "amp_short_vectors/Concurrency::graphics::unorm_2"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator-="
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator/="
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::yx"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::gr"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::r"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator-"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::get_x"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::g"
  - "amp_short_vectors/Concurrency::graphics::unnorm_2::operator++"
dev_langs: 
  - "C++"
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# unorm_2 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示兩個不帶正負號的正規的短向量。  
  
## 語法  
  
```  
class unorm_2;  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`value_type`||  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[unorm\_2::unorm\_2 建構函式](../Topic/unorm_2::unorm_2%20Constructor.md)|多載。  預設建構函式，初始化所有元素為 0 。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|unorm\_2::get\_x 方法。||  
|unorm\_2::get\_xy 方法。||  
|unorm\_2::get\_y 方法。||  
|unorm\_2::get\_yx 方法。||  
|unorm\_2::ref\_g 方法||  
|unorm\_2::ref\_r 方法||  
|unorm\_2::ref\_x 方法||  
|unorm\_2::ref\_y 方法||  
|unorm\_2::set\_x 方法。||  
|unorm\_2::set\_xy 方法。||  
|unorm\_2::set\_y 方法。||  
|unorm\_2::set\_yx 方法。||  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|unorm\_2 \-\- 運算子。||  
|unorm\_2 \*\= 運算子。||  
|unorm\_2 \/\= 運算子。||  
|unorm\_2 \+\+ 運算子。||  
|unorm\_2 \+\= 運算子。||  
|unorm\_2 \= 運算子。||  
|unorm\_2 \-\= 運算子。||  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|unorm\_2::size 常數||  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|unorm\_2::g 資料成員||  
|unorm\_2::gr 資料成員||  
|unorm\_2::r 資料成員||  
|unorm\_2::rg 資料成員||  
|unorm\_2::x 資料成員||  
|unorm\_2::xy 資料成員||  
|unorm\_2::y 資料成員||  
|unorm\_2::yx 資料成員||  
  
## 繼承階層架構  
 `unorm_2`  
  
## 需求  
 **標頭:** amp\_short\_vectors.h  
  
 **命名空間：**Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)