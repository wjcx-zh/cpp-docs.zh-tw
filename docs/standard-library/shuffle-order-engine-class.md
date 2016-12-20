---
title: "shuffle_order_engine 類別 | Microsoft Docs"
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
  - "shuffle_order_engine"
  - "std.tr1.shuffle_order_engine"
  - "tr1::shuffle_order_engine"
  - "tr1.shuffle_order_engine"
  - "std::tr1::shuffle_order_engine"
  - "random/std::tr1::shuffle_order_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shuffle_order_engine 類別"
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shuffle_order_engine 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

透過重新排列基底引擎傳回的值產生隨機序列。  
  
## 語法  
  
```  
template<class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### 參數  
 `Engine`  
 基底引擎類型。  
  
 `K`  
 **資料表大小**。 緩衝區 \(資料表\) 中的項目數。**前置條件**：`0 < K`  
  
## Members  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 如需引擎成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範例類別描述*「引擎配接器」*\(Engine Adaptor\)，其透過重新排列其基底引擎傳回的值產生值。 每個建構函式會將內部資料表填入基底引擎傳回的 `K` 值，並在要求值時，從資料表選取隨機項目。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)