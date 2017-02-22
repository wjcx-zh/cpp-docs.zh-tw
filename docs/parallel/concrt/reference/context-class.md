---
title: "Context 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::Context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Context 類別"
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# Context 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表執行內容的抽象概念。  
  
## 語法  
  
```  
class Context;  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Context::~Context 解構函式](../Topic/Context::~Context%20Destructor.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Context::Block 方法](../Topic/Context::Block%20Method.md)|封鎖目前的內容。|  
|[Context::CurrentContext 方法](../Topic/Context::CurrentContext%20Method.md)|傳回目前內容的指標。|  
|[Context::GetId 方法](../Topic/Context::GetId%20Method.md)|傳回內容的識別碼，在內容所屬的排程器中是唯一的。|  
|[Context::GetScheduleGroupId 方法](../Topic/Context::GetScheduleGroupId%20Method.md)|傳回內容目前正在處理之排程群組的識別碼。|  
|[Context::GetVirtualProcessorId 方法](../Topic/Context::GetVirtualProcessorId%20Method.md)|傳回目前正在執行內容之虛擬處理器的識別碼。|  
|[Context::Id 方法](../Topic/Context::Id%20Method.md)|傳回目前內容的識別碼，在目前內容所屬的排程器中是唯一的。|  
|[Context::IsCurrentTaskCollectionCanceling 方法](../Topic/Context::IsCurrentTaskCollectionCanceling%20Method.md)|傳回指示，表示目前正以內嵌方式執行於目前內容的工作集合是否正在取消或即將取消。|  
|[Context::IsSynchronouslyBlocked 方法](../Topic/Context::IsSynchronouslyBlocked%20Method.md)|決定內容是否以同步方式封鎖。  如果內容明確地執行導致封鎖的動作，會被視為同步封鎖。|  
|[Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)|在於該排程器中的其中一個虛擬處理器上執行的內容上叫用時，會將額外的虛擬處理器插入排程器中，期間為程式碼的區塊。|  
|[Context::ScheduleGroupId 方法](../Topic/Context::ScheduleGroupId%20Method.md)|傳回內容目前正在處理之排程群組的識別碼。|  
|[Context::Unblock 方法](../Topic/Context::Unblock%20Method.md)|解除封鎖內容，並讓它成為可執行。|  
|[Context::VirtualProcessorId 方法](../Topic/Context::VirtualProcessorId%20Method.md)|傳回正在執行目前內容之虛擬處理器的識別碼。|  
|[Context::Yield 方法](../Topic/Context::Yield%20Method.md)|產生執行，讓另一個內容可以執行。  如果沒有其他可產生的內容，排程器可能會產生至另一個作業系統執行緒。|  
  
## 備註  
 並行執行階段排程器 \(請參閱[排程器](../../../parallel/concrt/reference/scheduler-class.md)\) 使用執行內容來執行應用程式佇列至該排程器中的工作。  Win32 執行緒是在作業系統視窗上執行內容的範例。  
  
 排程器的並行存取層級隨時都等於資源管理員授與它的虛擬處理器的數目。  虛擬處理器是處理資源的抽象概念，對應於基礎系統的硬體執行緒。  在指定時間內，一個虛擬處理器只能執行一個排程器內容。  
  
 排程器是合作性質，正在執行的內容若要進入等候狀態，隨時可以將其虛擬處理器產生在不同的內容中。  滿足其等候時，便無法繼續進行，直到排程器中可用的虛擬處理器開始執行它為止。  
  
## 繼承階層架構  
 `Context`  
  
## 需求  
 **標頭：** concrt.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 類別](../../../parallel/concrt/reference/scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)