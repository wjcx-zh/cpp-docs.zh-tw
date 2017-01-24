---
title: "IExecutionContext 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IExecutionContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionContext 結構"
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IExecutionContext 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

執行內容的介面，可執行逾指定的虛擬處理器，也可以切換內容。  
  
## 語法  
  
```  
struct IExecutionContext;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IExecutionContext::Dispatch 方法](../Topic/IExecutionContext::Dispatch%20Method.md)|方法，當執行緒 Proxy 開始執行特定的執行內容時呼叫。  這應該是您的排程器的主要工作處理序常式。|  
|[IExecutionContext::GetId 方法](../Topic/IExecutionContext::GetId%20Method.md)|傳回執行內容排程器的唯一識別碼。|  
|[IExecutionContext::GetProxy 方法](../Topic/IExecutionContext::GetProxy%20Method.md)|傳回正在執行這個內容之執行緒 Proxy 的介面。|  
|[IExecutionContext::GetScheduler 方法](../Topic/IExecutionContext::GetScheduler%20Method.md)|傳回此執行內容所屬之排程器的介面。|  
|[IExecutionContext::SetProxy 方法](../Topic/IExecutionContext::SetProxy%20Method.md)|將執行緒 Proxy 與此執行內容相關聯。  相關的執行緒 Proxy 會在此方法開始執行內容的 `Dispatch` 方法之前叫用此方法。|  
  
## 備註  
 如果您要實作與並行執行階段的資源管理員互動的自訂排程器，您必須實作 `IExecutionContext` 介面。  資源管理員所建立的執行緒會藉由執行 `IExecutionContext::Dispatch` 方法來代表您的排程器執行工作。  
  
## 繼承階層架構  
 `IExecutionContext`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler 結構](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy 結構](../../../parallel/concrt/reference/ithreadproxy-structure.md)