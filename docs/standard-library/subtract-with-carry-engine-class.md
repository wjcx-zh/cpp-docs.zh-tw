---
title: "subtract_with_carry_engine 類別 | Microsoft Docs"
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
  - "tr1.subtract_with_carry_engine"
  - "std::tr1::subtract_with_carry_engine"
  - "random/std::tr1::subtract_with_carry_engine"
  - "subtract_with_carry_engine"
  - "tr1::subtract_with_carry_engine"
  - "std.tr1.subtract_with_carry_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subtract_with_carry_engine 類別"
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# subtract_with_carry_engine 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用帶進位減法 \(延隔 Fibonacci\) 演算法，以產生隨機序列。  
  
## 語法  
  
```  
template<class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### 參數  
 `UIntType`  
 不帶正負號的整數結果類型。 可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
 `W`  
 **字組大小**。 狀態序列的每個字組大小 \(位元\)。**前置條件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **短延隔**。 整數值數目。**前置條件**：`0 < S < R`  
  
 `R`  
 **長延隔**。 決定所產生數列中的週期。  
  
## Members  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` 是一個成員常數，定義為 `19780503u`，用做 `subtract_with_carry_engine::seed` 的預設參數值以及單一值建構函式。|||  
  
 如需引擎成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 `substract_with_carry_engine` 範本類別是針對 [linear\_congruential\_engine](../standard-library/linear-congruential-engine-class.md) 的改良。 但這些引擎都不像 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md) 一樣快，且具有高品質的結果。  
  
 此引擎使用週期關聯 \(*period*\) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` 來產生使用者指定之不帶正負號整數類型的值，其中，如果 `cy(i)`，則 `1` 的值為 `x(i - S) - x(i - R) - cy(i - 1) < 0`，否則為 `0`，而 `M` 的值為 `2`<sup>W</sup>。 引擎的狀態是一個進位指標加上 `R` 值。 這些值包含已至少呼叫 `R``operator()` 次時所傳回的最後一個 `R` 值，否則為已傳回的 `N` 值，以及種子的最後一個 `R - N` 值。  
  
 範本引數 `UIntType` 必須夠大，才能保留最多 `M - 1` 個值。  
  
 雖然您可以直接建構從此引擎的產生器，您也可以使用這些預先定義的 typedef 的其中一個︰  
  
 `ranlux24_base`︰ 做為基底 `ranlux24`。  
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`︰ 做為基底 `ranlux48`。  
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 如需帶進位減法引擎演算法的詳細資訊，請參閱 Wikipedia 文章 [延隔 Fibonacci 產生器](http://go.microsoft.com/fwlink/?LinkId=402445)。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)