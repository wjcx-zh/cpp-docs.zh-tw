---
title: "simple_partitioner 類別 | Microsoft Docs"
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
  - "ppl/concurrency::simple_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "simple_partitioner 類別"
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# simple_partitioner 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`simple_partitioner`類別代表靜態分割陣列範圍的`parallel_for`。  Partitioner 劃分範圍區塊 \(chunk\)，每個區塊已配備的區塊大小所指定的重複次數。  
  
## 語法  
  
```  
class simple_partitioner;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[simple\_partitioner::simple\_partitioner 建構函式](../Topic/simple_partitioner::simple_partitioner%20Constructor.md)|建構 `simple_partitioner` 物件。|  
|[simple\_partitioner::~simple\_partitioner 解構函式](../Topic/simple_partitioner::~simple_partitioner%20Destructor.md)|終結 `simple_partitioner` 物件。|  
  
## 繼承階層架構  
 `simple_partitioner`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)