---
title: "IUMSScheduler 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSScheduler 結構"
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IUMSScheduler 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

工作排程器抽象概念的介面，需要並行執行階段的資源管理員將使用者模式可排程的 \(UMS\) 執行緒傳遞給它。  資源管理員會使用這個介面與 UMS 執行緒排程器進行通訊。  `IUMSScheduler` 介面繼承自 `IScheduler` 介面。  
  
## 語法  
  
```  
struct IUMSScheduler : public IScheduler;  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[IUMSScheduler::SetCompletionList 方法](../Topic/IUMSScheduler::SetCompletionList%20Method.md)|指派 `IUMSCompletionList` 介面給 UMS 執行緒排程器。|  
  
## 備註  
 如果您要實作與資源管理員通訊的自訂排程器，而且想將 UMS 執行緒遞送至排程器，而非遞送一般的 Win32 執行緒，請提供 `IUMSScheduler` 介面的實作。  此外，您應將排程器原則機碼 `SchedulerKind` 的原則值設為  `UmsThreadDefault`。  如果原則指定 UMS 執行緒，則做為參數傳遞至 [IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md) 方法的 `IScheduler` 介面必須是 `IUMSScheduler` 介面。  
  
 資源管理員只能再具有 UMS 功能的作業系統上傳遞 UMS 執行緒。64 位元作業系統與 Windows 7 版 \(含以上\) 支援 UMS 執行緒。  如果您建立的排程器原則將 `SchedulerKind` 索引鍵設定為 `UmsThreadDefault` 值，且基礎平台不支援 UMS，該原則中 `SchedulerKind` 索引鍵的值就會變更為 `ThreadScheduler` 值。  您必須先讀回此原則值，才會收到 UMS 執行緒。  
  
 `IUMSScheduler` 介面是排程器和資源管理員雙向通訊管道的其中一端。  另一端是以資源管理員所實作的 `IResourceManager` 和 `ISchedulerProxy` 介面表示。  
  
## 繼承階層  
 [IScheduler](../../../parallel/concrt/reference/ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [IScheduler 結構](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IUMSCompletionList 結構](../../../parallel/concrt/reference/iumscompletionlist-structure.md)   
 [IResourceManager 結構](../../../parallel/concrt/reference/iresourcemanager-structure.md)