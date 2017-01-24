---
title: "extent 類別 (C++ AMP) | Microsoft Docs"
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
  - "amp/Concurrency::extent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extent 結構"
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# extent 類別 (C++ AMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表 *N* 整數值的向量，指定以 0 為原點的 *N* 維空間的範圍。  向量中的值會從最重要至最不重要排列。  
  
## 語法  
  
```  
template <  
   int _Rank>  
class extent;  
```  
  
#### 參數  
 `_Rank`  
 `extent` 物件的順位。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[extent::extent 建構函式](../Topic/extent::extent%20Constructor.md)|初始化 `extent` 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[extent::contains 方法](../Topic/extent::contains%20Method.md)|確認指定的 `extent` 物件具有指定的陣序。|  
|[extent::size 方法](../Topic/extent::size%20Method.md)|傳回範圍的總線性大小 \(以項目數為單位\) 。|  
|[extent::tile 方法](../Topic/extent::tile%20Method.md)|用指定的 tile 維度產生 `tiled_extent` 物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[extent::operator\- 運算子](../Topic/extent::operator-%20Operator.md)|傳回由對應的 `extent` 項目減去 `index` 項目所建立的新的 `extent` 物件。|  
|[extent::operator\-\- 運算子](../Topic/extent::operator--%20Operator.md)|遞減 `extent` 物件中的每個項目。|  
|[extent::operator\(mod\)\= 運算子](../Topic/extent::operator\(mod\)=%20Operator.md)|計算 `extent` 物件中每個項目除以某個數字時的模數 \(餘數\)。|  
|[extent::operator\*\= 運算子](../Topic/extent::operator*=%20Operator.md)|將每個 `extent` 物件中的項目乘以一數。|  
|[extent::operator\/\= 運算子](../Topic/extent::operator-=%20Operator1.md)|將 `extent` 物件中的每個項目除以數值。|  
|[extent::operatorOperator](../Topic/extent::operatorOperator.md)|傳回位於指定索引的項目。|  
|[extent::operator\+ 運算子](../Topic/extent::operator+%20Operator.md)|傳回由對應的 `index` 和 `extent` 項目相加所建立的新的 `extent` 物件。|  
|[extent::operator\+\+ 運算子](../Topic/extent::operator++%20Operator.md)|遞增 `extent` 物件中的每個項目。|  
|[extent::operator\+\= 運算子](../Topic/extent::operator+=%20Operator.md)|將 `extent` 物件的每個項目加上指定的數值。|  
|[extent::operator\= 運算子](../Topic/extent::operator=%20Operator.md)|將另一個 `extent` 物件的內容複製到這一個。|  
|[extent::operator\-\= 運算子](../Topic/extent::operator-=%20Operator2.md)|將 `extent` 物件中的每個項目減去指定的數值。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[extent::rank 常數](../Topic/extent::rank%20Constant.md)|取得 `extent` 物件的陣序。|  
  
## 繼承階層架構  
 `extent`  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)