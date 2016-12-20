---
title: "IThreadProxy 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadProxy 結構"
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: 21
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IThreadProxy 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

執行緒的抽象概念。  視您所建立的排程器的 `SchedulerType` 原則機碼，資源管理員會授與您由一般 Win32 執行緒或使用者模式可排程 \(UMS\) 執行緒備份的執行緒 Proxy。  安裝 Windows 7 \(含以上\) 版本的 64 位元作業系統支援 UMS 執行緒。  
  
## 語法  
  
```  
struct IThreadProxy;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IThreadProxy::GetId 方法](../Topic/IThreadProxy::GetId%20Method.md)|傳回執行緒 Proxy 的唯一識別碼。|  
|[IThreadProxy::SwitchOut 方法](../Topic/IThreadProxy::SwitchOut%20Method.md)|解除關聯的內容，從底層的虛擬處理器根目錄。|  
|[IThreadProxy::SwitchTo 方法](../Topic/IThreadProxy::SwitchTo%20Method.md)|執行從目前正在執行內容的合作內容切換至另一個內容。|  
|[IThreadProxy::YieldToSystem 方法](../Topic/IThreadProxy::YieldToSystem%20Method.md)|造成呼叫執行緒執行目前處理器上已就緒可執行的其他執行緒。  作業系統會選取下一個要執行的執行緒。|  
  
## 備註  
 執行緒 Proxy 會結合於由介面 `IExecutionContext` 代表的執行內容，做為分派工作的方法。  
  
## 繼承階層架構  
 `IThreadProxy`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext 結構](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IScheduler 結構](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IVirtualProcessorRoot 結構](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)