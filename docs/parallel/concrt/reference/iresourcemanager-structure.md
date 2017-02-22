---
title: "IResourceManager 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IResourceManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IResourceManager 結構"
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# IResourceManager 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

並行執行階段資源管理員的介面。  這是排程器用來與資源管理員通訊的介面。  
  
## 語法  
  
```  
struct IResourceManager;  
```  
  
## 成員  
  
### 公用列舉  
  
|名稱|說明|  
|--------|--------|  
|[IResourceManager::OSVersion 列舉](../Topic/IResourceManager::OSVersion%20Enumeration.md)|代表作業系統版本的列舉型別。|  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[IResourceManager::CreateNodeTopology 方法](../Topic/IResourceManager::CreateNodeTopology%20Method.md)|只會出現在執行階段的偵錯建置中，此方法是測試勾點，設計用於輔助不同硬體拓樸上的資源管理員，不需要符合組態的實際硬體。  使用執行階段正式版本組建時，這個方法會傳回而不執行任何動作。|  
|[IResourceManager::GetAvailableNodeCount 方法](../Topic/IResourceManager::GetAvailableNodeCount%20Method.md)|傳回節點數目可用的資源管理員。|  
|[IResourceManager::GetFirstNode 方法](../Topic/IResourceManager::GetFirstNode%20Method.md)|傳回第一個節點的列舉型別順序所定義資源管理員。|  
|[IResourceManager::Reference 方法](../Topic/IResourceManager::Reference%20Method.md)|遞增資源管理員執行個體上的參考計數。|  
|[IResourceManager::RegisterScheduler 方法](../Topic/IResourceManager::RegisterScheduler%20Method.md)|在資源管理員註冊排程器。  一旦註冊排程氣後，排程器應使用所傳回的 `ISchedulerProxy` 介面與資源管理員通訊。|  
|[IResourceManager::Release 方法](../Topic/IResourceManager::Release%20Method.md)|遞減資源管理員執行個體上的參考計數。  資源管理員的參考計數達到 `0` 時，就會被終結。|  
  
## 備註  
 使用 [CreateResourceManager](../Topic/CreateResourceManager%20Function.md) 函式來取得單一資源管理員執行個體的介面。  方法會遞增資源管理員上的參考計數，當您完成使用資源管理員時，應叫用 [IResourceManager::Release](../Topic/IResourceManager::Release%20Method.md) 方法以釋放參考。  通常，您建立的每個排程器會在建立時叫用這個方法，然後在關機後釋放參考到資源管理員。  
  
## 繼承階層  
 `IResourceManager`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISchedulerProxy 結構](../../../parallel/concrt/reference/ischedulerproxy-structure.md)   
 [IScheduler 結構](../../../parallel/concrt/reference/ischeduler-structure.md)