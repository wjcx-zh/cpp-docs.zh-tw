---
title: "index 類別 | Microsoft Docs"
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
  - "amp/Concurrency::index"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "index 結構"
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# index 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

定義 *N* 維索引點。  
  
## 語法  
  
```  
template <  
   int _Rank  
>  
class index;  
```  
  
#### 參數  
 `_Rank`  
 維度的順位或數目。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[index::index 建構函式](../Topic/index::index%20Constructor.md)|初始化 `index` 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[index::operator\-\- 運算子](../Topic/index::operator--%20Operator.md)|遞減 `index` 物件中的每個項目。|  
|[index::operator\(mod\)\= 運算子](../Topic/index::operator\(mod\)=%20Operator.md)|計算 `index` 物件中每個項目除以某個數字時的模數 \(餘數\)。|  
|[index::operator\*\= 運算子](../Topic/index::operator*=%20Operator.md)|將每個 `index` 物件中的項目乘以一數。|  
|[index::operator\/\= 運算子](../Topic/index::operator-=%20Operator2.md)|將 `index` 物件中的每個項目除以數值。|  
|[index::operatorOperator](../Topic/index::operatorOperator.md)|傳回位於指定索引的項目。|  
|[index::operator\+\+ 運算子](../Topic/index::operator++%20Operator.md)|遞增 `index` 物件中的每個項目。|  
|[index::operator\+\= 運算子](../Topic/index::operator+=%20Operator.md)|將 `index` 物件的每個項目加上指定的數值。|  
|[index::operator\= 運算子](../Topic/index::operator=%20Operator.md)|將指定之 `index` 物件的內容複製到這個物件。|  
|[index::operator\-\= 運算子](../Topic/index::operator-=%20Operator1.md)|將 `index` 物件中的每個項目減去指定的數值。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[index::rank 常數](../Topic/index::rank%20Constant.md)|儲存 `index` 物件的順位。|  
  
## 繼承階層架構  
 `index`  
  
## 備註  
 `index` 結構代表 *N* 個整數的座標向量，會在 *N* 維空間中指定一個唯一的位置。  向量中的值會從最重要至最不重要排列。  您可以使用 [index::operator\= 運算子](../Topic/index::operator=%20Operator.md) 來擷取元件的值。  
  
## 需求  
 **標頭：**amp.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)