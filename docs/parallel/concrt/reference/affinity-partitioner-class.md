---
title: "affinity_partitioner 類別 | Microsoft Docs"
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
  - "ppl/concurrency::affinity_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "affinity_partitioner 類別"
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# affinity_partitioner 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`affinity_partitioner`類別是類似於`static_partitioner`類別，但它會快取親和性提高其選擇的對應子範圍與背景工作執行緒。  針對相同的資料集合，會重新執行迴圈並的資料放在快取中時，它可以明顯改善效能。  請注意，相同`affinity_partitioner`物件使用方式必須執行特定的資料集合，可受益於資料位置上的平行迴圈的後續的反覆項目。  
  
## 語法  
  
```  
class affinity_partitioner;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[affinity\_partitioner::affinity\_partitioner 建構函式](../Topic/affinity_partitioner::affinity_partitioner%20Constructor.md)|建構 `affinity_partitioner` 物件。|  
|[affinity\_partitioner::~affinity\_partitioner 解構函式](../Topic/affinity_partitioner::~affinity_partitioner%20Destructor.md)|終結 `affinity_partitioner` 物件。|  
  
## 繼承階層架構  
 `affinity_partitioner`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)