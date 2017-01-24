---
title: "scheduler_not_attached 類別 | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_not_attached"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_not_attached 類別"
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_not_attached 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

這個類別會描述時，它需要排程器會附加到目前的內容來執行作業，並有一個不會擲回例外狀況。  
  
## 語法  
  
```  
class scheduler_not_attached : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[scheduler\_not\_attached::scheduler\_not\_attached 建構函式](../Topic/scheduler_not_attached::scheduler_not_attached%20Constructor.md)|多載。  建構 `scheduler_not_attached` 物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `scheduler_not_attached`  
  
## 需求  
 **標頭：** concrt.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)