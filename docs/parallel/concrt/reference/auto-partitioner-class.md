---
title: "auto_partitioner 類別 | Microsoft Docs"
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
  - "ppl/concurrency::auto_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_partitioner 類別"
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_partitioner 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`auto_partitioner`類別代表預設的方法`parallel_for`， `parallel_for_each`和`parallel_transform`用來分割它們會反覆執行到的範圍。  這個方法的資料分割 employes 竊取負載平衡的範圍，以及每一位重複取消。  
  
## 語法  
  
```  
class auto_partitioner;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[auto\_partitioner::auto\_partitioner 建構函式](../Topic/auto_partitioner::auto_partitioner%20Constructor.md)|建構 `auto_partitioner` 物件。|  
|[auto\_partitioner::~auto\_partitioner 解構函式](../Topic/auto_partitioner::~auto_partitioner%20Destructor.md)|終結 `auto_partitioner` 物件。|  
  
## 繼承階層架構  
 `auto_partitioner`  
  
## 需求  
 **標頭：** ppl.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)