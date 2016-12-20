---
title: "independent_bits_engine 類別 | Microsoft Docs"
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
  - "std.tr1.independent_bits_engine"
  - "std::tr1::independent_bits_engine"
  - "tr1::independent_bits_engine"
  - "tr1.independent_bits_engine"
  - "independent_bits_engine"
  - "random/std::tr1::independent_bits_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "independent_bits_engine 類別"
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# independent_bits_engine 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

重新封裝基底引擎所傳回值的位元，以產生具有指定位元數的隨機一連串數字。  
  
## 語法  
  
```  
template<class Engine, size_t W, class UIntType> class independent_bits_engine;  
```  
  
#### 參數  
 `Engine`  
 基底引擎類型。  
  
 `W`  
 **字組大小**。  每個所產生數字的大小 \(位元\)。  **前置條件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 不帶正負號的整數結果類型。  如需可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## Members  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 如需引擎成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述*「引擎配接器」*\(engine adaptor\)，其透過重新封裝來自其基底引擎所傳回值的位元以產生值，這樣會導致 `W` 位元值。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)