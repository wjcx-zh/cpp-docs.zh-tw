---
title: "event 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event 類別"
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# event 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

並行執行階段明確察覺的手動重設事件。  
  
## 語法  
  
```  
class event;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[event::~event 解構函式](../Topic/event::~event%20Destructor.md)|終結事件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[event::reset 方法](../Topic/event::reset%20Method.md)|將事件重設為未發出訊號的狀態。|  
|[event::set 方法](../Topic/event::set%20Method.md)|以信號通知事件。|  
|[event::wait 方法](../Topic/event::wait%20Method.md)|等候事件成為已收到信號。|  
|[event::wait\_for\_multiple 方法](../Topic/event::wait_for_multiple%20Method.md)|等候多個事件成為已收到信號。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[event::timeout\_infinite 常數](../Topic/event::timeout_infinite%20Constant.md)|值，表示等候應該永遠不會逾時。|  
  
## 備註  
 如需詳細資訊，請參閱[同步處理資料結構](../../../parallel/concrt/synchronization-data-structures.md)。  
  
## 繼承階層架構  
 `event`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)