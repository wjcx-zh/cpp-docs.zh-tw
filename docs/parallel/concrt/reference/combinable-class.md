---
title: "combinable 類別 | Microsoft Docs"
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
  - "ppl/concurrency::combinable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combinable 類別"
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# combinable 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`combinable<T>` 物件適用於提供資料的執行緒私用複本，在平行演算法期間執行無鎖定的執行緒\-本機子運算。  在平行作業結尾處，可以將執行緒私用子運算合併於最終結果。  這個類別可以用來代替共用變數，而且如果該共用變數有許多爭用情形，則可能可以改進效能。  
  
## 語法  
  
```  
template<  
   typename _Ty  
>  
class combinable;  
```  
  
#### 參數  
 `_Ty`  
 最後合併結果的資料型別。  型別必須具有複製建構函式和預設的建構函式。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[combinable::combinable 建構函式](../Topic/combinable::combinable%20Constructor.md)|多載。  建構新的 `combinable` 物件。|  
|[combinable::~combinable 解構函式](../Topic/combinable::~combinable%20Destructor.md)|終結 `combinable` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[combinable::clear 方法](../Topic/combinable::clear%20Method.md)|清除先前使用方式的任何中繼運算結果。|  
|[combinable::combine 方法](../Topic/combinable::combine%20Method.md)|藉由呼叫提供的結合仿函數，從一組執行緒本機子運算計算最終值。|  
|[combinable::combine\_each 方法](../Topic/combinable::combine_each%20Method.md)|藉由每個執行緒本機子運算呼叫一次提供的結合仿函數，從一組執行緒本機子運算計算最終值。  函式物件會累積最終結果。|  
|[combinable::local 方法](../Topic/combinable::local%20Method.md)|多載。  傳回執行緒私用子運算的參考。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[combinable::operator\= 運算子](../Topic/combinable::operator=%20Operator.md)|從另一個 `combinable` 物件指派到 `combinable` 物件。|  
  
## 備註  
 如需詳細資訊，請參閱 [平行容器和物件](../../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 繼承階層架構  
 `combinable`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)