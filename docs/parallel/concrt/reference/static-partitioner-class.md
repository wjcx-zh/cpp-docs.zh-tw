---
title: "static_partitioner 類別 | Microsoft Docs"
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
  - "ppl/concurrency::static_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "static_partitioner 類別"
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# static_partitioner 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`static_partitioner`類別代表靜態分割陣列範圍的`parallel_for`。  Partitioner 區分為多個區塊，因為會有工作者可以使用 underyling 排程器範圍。  
  
## 語法  
  
```  
class static_partitioner;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[static\_partitioner::static\_partitioner 建構函式](../Topic/static_partitioner::static_partitioner%20Constructor.md)|建構 `static_partitioner` 物件。|  
|[static\_partitioner::~static\_partitioner 解構函式](../Topic/static_partitioner::~static_partitioner%20Destructor.md)|終結 `static_partitioner` 物件。|  
  
## 繼承階層架構  
 `static_partitioner`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)