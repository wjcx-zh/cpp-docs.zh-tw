---
title: "IVirtualProcessorRoot 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IVirtualProcessorRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IVirtualProcessorRoot 結構"
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IVirtualProcessorRoot 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。  
  
## 語法  
  
```  
struct IVirtualProcessorRoot : public IExecutionResource;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IVirtualProcessorRoot::Activate 方法](../Topic/IVirtualProcessorRoot::Activate%20Method.md)|會導致與執行內容介面 `pContext` 相關的執行緒 Proxy 開始在此虛擬處理器根上執行。|  
|[IVirtualProcessorRoot::Deactivate 方法](../Topic/IVirtualProcessorRoot::Deactivate%20Method.md)|會導致目前正在這個虛擬處理器根上執行的在執行緒 Proxy 停止分派執行內容。  執行緒 Proxy 會繼續執行 `Activate` 方法呼叫。|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible 方法](../Topic/IVirtualProcessorRoot::EnsureAllTasksVisible%20Method.md)|造成存放在個別處理器之記憶體階層中的資料顯示在系統的所有處理器上。  它可確保在方法傳回前已在所有處理器上執行完整的記憶體柵欄。|  
|[IVirtualProcessorRoot::GetId 方法](../Topic/IVirtualProcessorRoot::GetId%20Method.md)|傳回虛擬處理器根的唯一識別項。|  
  
## 備註  
 每個虛擬處理器根都有一個相關的執行資源。  `IVirtualProcessorRoot` 介面繼承自 [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md) 介面。  多個虛擬處理器根可能會對應到相同的基礎硬體執行緒。  
  
 資源管理員會回應資源要求，將虛擬處理器根授與排程器。  排程器可以使用虛擬處理器根來執行，方法是以執行內容啟用該工作。  
  
## 繼承階層架構  
 [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)