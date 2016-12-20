---
title: "ISchedulerProxy 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::ISchedulerProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISchedulerProxy 結構"
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISchedulerProxy 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。  
  
## 語法  
  
```  
struct ISchedulerProxy;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ISchedulerProxy::BindContext 方法](../Topic/ISchedulerProxy::BindContext%20Method.md)|將執行內容與執行緒 Proxy 相關聯 \(如果尚未具備任何關聯\)。|  
|[ISchedulerProxy::CreateOversubscriber 方法](../Topic/ISchedulerProxy::CreateOversubscriber%20Method.md)|在與現有執行資源相關的硬體執行緒上建立新的虛擬處理器。|  
|[ISchedulerProxy::RequestInitialVirtualProcessors 方法](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)|要求初始配置虛擬處理器根。  每個虛擬處理器根都代表能夠執行其中一個可執行排程器工作的執行緒。|  
|[ISchedulerProxy::Shutdown 方法](../Topic/ISchedulerProxy::Shutdown%20Method.md)|通知資源管理員排程器正在關閉。  這會導致資源管理員立即重新收回授與排程器的所有資源。|  
|[ISchedulerProxy::SubscribeCurrentThread 方法](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)|在資源管理員註冊目前的執行緒，並將該執行緒與此排程器產生關聯。|  
|[ISchedulerProxy::UnbindContext 方法](../Topic/ISchedulerProxy::UnbindContext%20Method.md)|解除執行緒與 `pContext` 參數所指定之執行內容的關聯，並將其傳回執行緒 Proxy Factory 的可用集區。  只能在透過 [ISchedulerProxy::BindContext](../Topic/ISchedulerProxy::BindContext%20Method.md) 方法繫結且尚未透過成為 [IThreadProxy::SwitchTo](../Topic/IThreadProxy::SwitchTo%20Method.md) 方法呼叫的 `pContext` 參數啟動時，才能在執行內容呼叫這個方法。|  
  
## 備註  
 資源管理員會使用[IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md)方法，將`ISchedulerProxy` 介面傳遞至在資源管理員中註冊的所有排程器。  
  
## 繼承階層架構  
 `ISchedulerProxy`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler 結構](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy 結構](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot 結構](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager 結構](../../../parallel/concrt/reference/iresourcemanager-structure.md)