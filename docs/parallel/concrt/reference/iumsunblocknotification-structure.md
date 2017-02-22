---
title: "IUMSUnblockNotification 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSUnblockNotification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSUnblockNotification 結構"
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# IUMSUnblockNotification 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表資源管理員發出的通知，表示封鎖及觸發傳回排程器指派排程內容的執行緒 Proxy 已解除鎖定，而且已準備好進行排程。  若重新排程從 `GetContext` 方法傳回之執行緒 Proxy 的相關執行內容，則此介面不正確。  
  
## 語法  
  
```  
struct IUMSUnblockNotification;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IUMSUnblockNotification::GetContext 方法](../Topic/IUMSUnblockNotification::GetContext%20Method.md)|傳回與已解除鎖定之執行緒 Proxy 相關的執行內容的 `IExecutionContext` 介面。  一旦這個方法傳回，並透過 `IThreadProxy::SwitchTo` 方法呼叫重新排程基礎的執行內容，這個介面已不再有效。|  
|[IUMSUnblockNotification::GetNextUnblockNotification 方法](../Topic/IUMSUnblockNotification::GetNextUnblockNotification%20Method.md)|傳回從方法 `IUMSUnblockNotification` 傳回之鏈結中的下一個 `IUMSCompletionList::GetUnblockNotifications` 介面。|  
  
## 繼承階層架構  
 `IUMSUnblockNotification`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 結構](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSCompletionList 結構](../../../parallel/concrt/reference/iumscompletionlist-structure.md)