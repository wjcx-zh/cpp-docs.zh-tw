---
title: "mersenne_twister_engine 類別 | Microsoft Docs"
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
  - "random/std::tr1::mersenne_twister_engine"
  - "tr1.mersenne_twister_engine"
  - "std.tr1.mersenne_twister_engine"
  - "std::tr1::mersenne_twister_engine"
  - "tr1::mersenne_twister_engine"
  - "mersenne_twister_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mersenne_twister_engine 類別"
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mersenne_twister_engine 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據梅森旋轉演算法，產生高品質隨機整數序列。  
  
## 語法  
  
```  
template<class UIntType,   
    size_t W, size_t N, size_t M, size_t R,  
    UIntType A, size_t U, UIntType D, size_t S,  
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>  
class mersenne_twister_engine;  
```  
  
#### 參數  
 `UIntType`  
 不帶正負號的整數結果類型。 可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
 `W`  
 **字組大小**。 狀態序列的每個字組大小 \(位元\)。**前置條件**：`2u < W ≤ numeric_limits<UIntType>::digits`  
  
 `N`  
 **狀態大小**。 狀態序列中的元素數 \(值\)。  
  
 `M`  
 **移位大小**。 要在每個旋轉期間跳過的元素數。**前置條件**：`0 < M ≤ N`  
  
 `R`  
 **遮罩位元**。**前置條件**：`R ≤ W`  
  
 `A`  
 **XOR 遮罩**。**前置條件**：`A ≤ (1u<<W) - 1u`  
  
 `U`, `S`, `T`, `L`  
 **調和移位參數**。 用做編碼 \(調和\) 期間的移位值。 前置條件：`U,S,T,L ≤ W`  
  
 `D`, `B`, `C`  
 **調和位元遮罩參數**。 用做編碼 \(調和\) 期間的位元遮罩值。 前置條件：`D,B,C ≤ (1u<<W) - 1u`  
  
 `F`  
 **初始化乘數**。 用於協助初始化序列。 前置條件：`F ≤ (1u<<W) - 1u`  
  
## Members  
  
||||  
|-|-|-|  
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|  
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|  
  
 `default_seed` 是一個成員常數，定義為 `5489u`，用做 `mersenne_twister_engine::seed` 的預設參數值以及單一值建構函式。  
  
 如需引擎成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述亂數引擎，其傳回封閉間隔的值 \[`0`, ，`2`<sup>W</sup> \- `1`\]。 它會保留具有 `W * (N - 1) + R` 位元的大整數值。 它一次會從這個大數值擷取 `W` 位元，而且使用所有位元時，它會使用移位和混合位元旋轉大數值，使其具有一組要從中擷取的新位元。 引擎的狀態是最後 `N``W`\-位元值，如果使用 `operator()` 至少呼叫 `N` 時間，否則 `M``W`\-位元已使用的值，而最後 `N - M` 種子的值。  
  
 產生器會旋轉它所保留的大數值，方法是使用移位值 `N` 和 `M` 所定義的已旋轉一般化回饋移位暫存器、旋轉值 `R` 和條件式 XOR 遮罩 `A`。 此外，還會根據值 `U`、`D`、`S`、`B`、`T`、`C` 和 `L` 所定義的位元編碼矩陣，來編碼 \(調和\) 原始移位暫存器的位元。  
  
 樣板引數 `UIntType` 必須夠大，才能保留最多值 `2`<sup>W</sup> \- `1`。 其他範本引數的值必須滿足下列需求：`2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`。  
  
 雖然您可以直接建構從此引擎的產生器，建議您在使用這些預先定義的 typedef 的其中一個︰  
  
 `mt19937`: 32 位元梅森旋轉引擎 （Matsumoto 和 Nishimura，1998 年）。  
  
```  
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,   
    31, 0x9908b0df,   
    11, 0xffffffff,   
    7, 0x9d2c5680,   
    15, 0xefc60000,   
    18, 1812433253> mt19937;  
```  
  
 `mt19937_64`: 64 位元梅森旋轉引擎 （Matsumoto 和 nishimura，2000 年）。  
  
```  
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,   
    31, 0xb5026f5aa96619e9ULL,   
    29, 0x5555555555555555ULL,   
    17, 0x71d67fffeda60000ULL,   
    37, 0xfff7eee000000000ULL,   
    43, 6364136223846793005ULL> mt19937_64;  
```  
  
 如需梅森旋轉演算法的詳細資訊，請參閱 Wikipedia 文章 [梅森旋轉](http://go.microsoft.com/fwlink/?LinkId=402356)。  
  
## 範例  
 如需程式碼範例，請參閱[\<random\>](../standard-library/random.md)。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)