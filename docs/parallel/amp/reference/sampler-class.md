---
title: "sampler 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# sampler 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

取樣器類別會彙總要用於材質取樣的取樣組態資訊。  
  
## 語法  
  
```  
class sampler;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[sampler::sampler 建構函式](../Topic/sampler::sampler%20Constructor.md)|多載。  建構取樣器執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[sampler::get\_address\_mode 方法](../Topic/sampler::get_address_mode%20Method.md)|傳回和取樣器物件相關聯的 `address_mode`。|  
|[sampler::get\_border\_color 方法](../Topic/sampler::get_border_color%20Method.md)|傳回與取樣器物件相關聯的框線色彩。|  
|[sampler::get\_filter\_mode 方法](../Topic/sampler::get_filter_mode%20Method.md)|傳回和取樣器物件相關聯的 `filter_mode`。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[sampler::operator\= 運算子](../Topic/sampler::operator=%20Operator.md)|多載。  指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[sampler::address\_mode 資料成員](../Topic/sampler::address_mode%20Data%20Member.md)|取得 `sampler` 物件的位址模式。|  
|[sampler::border\_color 資料成員](../Topic/sampler::border_color%20Data%20Member.md)|取得 `sampler` 物件的框線色彩。|  
|[sampler::filter\_mode 資料成員](../Topic/sampler::filter_mode%20Data%20Member.md)|取得 `sampler` 物件的篩選模式。|  
  
## 繼承階層架構  
 `sampler`  
  
## 需求  
 **標頭：**amp\_graphics.h  
  
 **命名空間：**concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)