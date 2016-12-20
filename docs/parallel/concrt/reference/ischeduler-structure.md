---
title: "IScheduler 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IScheduler 結構"
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IScheduler 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

工作排程器抽象概念的介面。  並行執行階段的資源管理員會使用這個介面與工作排程器通訊。  
  
## 語法  
  
```  
struct IScheduler;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IScheduler::AddVirtualProcessors 方法](../Topic/IScheduler::AddVirtualProcessors%20Method.md)|提供排程器，以及一組供其使用的虛擬處理器根。  每個 `IVirtualProcessorRoot` 介面均代表執行單一執行緒的權限，此執行緒可以代表排程器執行工作。|  
|[IScheduler::GetId 方法](../Topic/IScheduler::GetId%20Method.md)|傳回排程器的唯一識別碼。|  
|[IScheduler::GetPolicy 方法](../Topic/IScheduler::GetPolicy%20Method.md)|傳回排程器的原則的複本。  如需排程器原則的詳細資訊，請參閱 [SchedulerPolicy](../../../parallel/concrt/reference/schedulerpolicy-class.md)。|  
|[IScheduler::NotifyResourcesExternallyBusy 方法](../Topic/IScheduler::NotifyResourcesExternallyBusy%20Method.md)|通知這個排程器，其他排程器現在使用陣列 `ppVirtualProcessorRoots` 中的一組虛擬處理器所代表的硬體執行緒。|  
|[IScheduler::NotifyResourcesExternallyIdle 方法](../Topic/IScheduler::NotifyResourcesExternallyIdle%20Method.md)|通知這個排程器，其他排程器並未使用陣列 `ppVirtualProcessorRoots` 中的一組虛擬處理器所代表的硬體執行緒。|  
|[IScheduler::RemoveVirtualProcessors 方法](../Topic/IScheduler::RemoveVirtualProcessors%20Method.md)|起始先前配置給此排程器的虛擬處理器根移除作業。|  
|[IScheduler::statistics 方法](../Topic/IScheduler::Statistics%20Method.md)|提供有關工作抵達及完成率的資訊，以及排程器佇列長度的變化。|  
  
## 備註  
 如果您要實作與資源管理員通訊的自訂排程器，請提供 `IScheduler` 介面的實作。  這個介面是排程器和資源管理員之間雙向通道的其中一端。  另一端是以資源管理員所實作的 `IResourceManager` 和 `ISchedulerProxy` 介面表示。  
  
## 繼承階層架構  
 `IScheduler`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey 列舉](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy 類別](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [IExecutionContext 結構](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IThreadProxy 結構](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](../../../parallel/concrt/reference/iresourcemanager-structure.md)