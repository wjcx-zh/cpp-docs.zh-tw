---
title: "uint_2 類別 | Microsoft Docs"
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
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::y"
  - "amp_short_vectors/Concurrency::graphics::uint_2::gr"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator-"
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator-="
  - "amp_short_vectors/Concurrency::graphics::uint_2::r"
  - "amp_short_vectors/Concurrency::graphics::uint_2::yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator--"
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator="
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator+="
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_y"
  - "amp_short_vectors/Concurrency::graphics::uint_2::xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::x"
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_xy"
  - "amp_short_vectors/Concurrency::graphics::uint_2::set_y"
  - "amp_short_vectors/Concurrency::graphics::uint_2"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator*="
  - "amp_short_vectors/Concurrency::graphics::uint_2::get_yx"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator/="
  - "amp_short_vectors/Concurrency::graphics::uint_2::g"
  - "amp_short_vectors/Concurrency::graphics::uint_2::operator++"
  - "amp_short_vectors/Concurrency::graphics::uint_2::rg"
dev_langs: 
  - "C++"
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uint_2 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示兩個不帶正負號的整數 \(Unsigned Short 的向量。  
  
## 語法  
  
```  
class uint_2;  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`value_type`||  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[uint\_2::uint\_2 建構函式](../Topic/uint_2::uint_2%20Constructor.md)|多載。  預設建構函式，初始化所有元素為 0 。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|uint\_2::get\_x 方法||  
|uint\_2::get\_xy 方法||  
|uint\_2::get\_y 方法||  
|uint\_2::get\_yx 方法||  
|uint\_2::ref\_g 方法||  
|uint\_2::ref\_r 方法||  
|uint\_2::ref\_x 方法||  
|uint\_2::ref\_y 方法||  
|uint\_2::set\_x 方法||  
|uint\_2::set\_xy 方法||  
|uint\_2::set\_y 方法||  
|uint\_2::set\_yx 方法||  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|float\_2 的 \-\- 運算子。||  
|uint\_2::operator 的 %\= 運算子。||  
|uint\_2::operator&\= 運算子。||  
|uint\_2::operator 的 \*\= 運算子。||  
|uint\_2::operator 的 \/\= 運算子。||  
|uint\_2::operator 的 ^\= 運算子。||  
|uint\_2::operator 的 &#124;\= 運算子。||  
|uint\_2::operator 的 ~ 運算子。||  
|uint\_2::operator 的 \+\+ 運算子。||  
|uint\_2::operator 的 \+\= 運算子。||  
|uint\_2::operator\<\<\= 運算子。||  
|uint\_2::operator 的 \= 運算子。||  
|uint\_2::operator 的 \-\= 運算子。||  
|uint\_2::operator\>\>\= 運算子。||  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[uint\_2::size 常數](../Topic/uint_2::size%20Constant.md)||  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|uint\_2::b 資料成員||  
|uint\_2::gr 資料成員||  
|uint\_2::r 資料成員||  
|uint\_2::rg 資料成員||  
|uint\_2::x 資料成員||  
|uint\_2::xy 資料成員||  
|uint\_2::y 資料成員||  
|uint\_2::yx 資料成員||  
  
## 繼承階層架構  
 `uint_2`  
  
## 需求  
 **標頭:** amp\_short\_vectors.h  
  
 **命名空間：**Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)