---
title: "linear_congruential_engine 類別 | Microsoft Docs"
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
  - "std.tr1.linear_congruential_engine"
  - "random/std::tr1::linear_congruential_engine"
  - "linear_congruential_engine"
  - "std::tr1::linear_congruential_engine"
  - "tr1.linear_congruential_engine"
  - "tr1::linear_congruential_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "linear_congruential_engine 類別"
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 21
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# linear_congruential_engine 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

依線性同餘演算法產生隨機序列。  
  
## 語法  
  
```  
template<class UIntType, UIntType A, UIntType C, UIntType M>  
class linear_congruential_engine{  
public:  
    // types  
    typedef UIntType result_type;  
  
    // engine characteristics  
    static constexpr result_type multiplier = a;  
    static constexpr result_type increment = c;  
    static constexpr result_type modulus = m;  
    static constexpr result_type min() { return c == 0u ? 1u: 0u; }  
    static constexpr result_type max() { return m - 1u; }  
    static constexpr result_type default_seed = 1u;  
  
    // constructors and seeding functions  
    explicit linear_congruential_engine(result_type s = default_seed);  
    template<class Sseq> explicit linear_congruential_engine(Sseq& q);  
    void seed(result_type s = default_seed);  
    template<class Sseq> void seed(Sseq& q);  
  
    // generating functions  
    result_type operator()();  
    void discard(unsigned long long z);  
};  
```  
  
#### 參數  
 `UIntType`  
 不帶正負號的整數結果類型。 可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
 `A`  
 **乘數**。**前置條件**：請參閱＜備註＞一節。  
  
 `C`  
 **遞增**。**前置條件**：請參閱＜備註＞一節。  
  
 `M`  
 **模數**。**前置條件**：請參閱備註。  
  
## Members  
  
||||  
|-|-|-|  
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|  
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|  
  
 `default_seed` 是一個成員常數，定義為 `1u`，用做 `linear_congruential_engine::seed` 的預設參數值以及單一值建構函式。  
  
 如需引擎成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 `linear_congruential_engine` 範本類別是最簡單的產生器引擎，但不具有最快或最高的品質。 和此引擎相較之下較為改進的是 [substract\_with\_carry\_engine](../standard-library/subtract-with-carry-engine-class.md)。 但這些引擎都不像 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md) 一樣快，且具有高品質的結果。  
  
 此引擎使用週期關聯 \(*「週期」*\(Period\)\) `x(i) = (A * x(i-1) + C) mod M`，產生使用者指定之不帶正負號的整數類型的值。  
  
 若 `M` 為零，則此模數作業所使用的值為 `numeric_limits<result_type>::max() + 1`。 引擎的狀態會是上次傳回的值；若沒有對 `operator()` 執行任何呼叫，則引擎的狀態是初始值。  
  
 若 `M` 不是零，則範本引數 `A` 和 `C` 的值必須小於 `M`。  
  
 雖然您可以直接建構從此引擎的產生器，您也可以使用其中一個這些預先定義的 typedef。  
  
 `minstd_rand0`: 1988年最低標準引擎 （Lewis、 Goodman 及 Miller，1969 年）。  
  
```  
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;  
```  
  
 `minstd_rand`︰ 升級的最低標準引擎 `minstd_rand0` （Park、 Miller 及 Stockmeyer，1993 年）。  
  
```  
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;  
```  
  
 如需線性同餘引擎演算法的詳細資訊，請參閱 Wikipedia 文章 [線性同餘方法產生器](http://go.microsoft.com/fwlink/?LinkId=402446)。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)