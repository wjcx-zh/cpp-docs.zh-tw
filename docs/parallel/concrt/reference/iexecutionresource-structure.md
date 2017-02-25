---
title: "IExecutionResource 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionResource 結構"
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# IExecutionResource 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

硬體執行緒的抽象概念。  
  
## 語法  
  
```  
struct IExecutionResource;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IExecutionResource::CurrentSubscriptionLevel 方法](../Topic/IExecutionResource::CurrentSubscriptionLevel%20Method.md)|傳回已啟動虛擬處理器根的數目，以及目前與這個執行資源代表之基礎硬體執行緒相關的已訂閱外部執行緒。|  
|[IExecutionResource::GetExecutionResourceId 方法](../Topic/IExecutionResource::GetExecutionResourceId%20Method.md)|傳回這個執行來源代表的硬體執行緒的唯一識別碼。|  
|[IExecutionResource::GetNodeId 方法](../Topic/IExecutionResource::GetNodeId%20Method.md)|傳回這個執行來源所屬的處理器節點的唯一識別碼。|  
|[IExecutionResource::Remove 方法](../Topic/IExecutionResource::Remove%20Method.md)|將這個執行資源傳回資源管理員。|  
  
## 備註  
 執行資源可以是獨立的，也可以與虛擬處理器根相關。  您應用程式中的執行緒建立執行緒訂閱時，會建立獨立的執行資源。  [ISchedulerProxy::SubscribeThread](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md) 和 [ISchedulerProxy::RequestInitialVirtualProcessors](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md) 方法會建立執行緒的訂閱，並傳回代表訂閱 `IExecutionResource` 介面。  建立執行緒訂閱是一種方法，可通知指定執行緒的資源管理員會與資源管理器指派給該排程器的虛擬處理器根依同參與佇列至排程器。  資源管理員會使用資訊來避免過度訂閱硬體執行緒。  
  
## 繼承階層架構  
 `IExecutionResource`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IVirtualProcessorRoot 結構](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [ISchedulerProxy::SubscribeCurrentThread 方法](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)   
 [ISchedulerProxy::RequestInitialVirtualProcessors 方法](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)