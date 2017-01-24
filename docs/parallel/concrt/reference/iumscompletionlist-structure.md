---
title: "IUMSCompletionList 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSCompletionList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSCompletionList 結構"
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSCompletionList 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表 UMS 完成清單。  當 UMS 執行緒封鎖時，會分派排程器的指定排程內容，以決定封鎖原始執行緒時要在基礎虛擬處理器根排程的內容。  原始執行緒解除封鎖時，作業系統會將它佇列到可透過此介面存取的完成清單中。  排程器可以在指派的排程內容或其搜尋工作的其他任何位置查詢完成清單。  
  
## 語法  
  
```  
struct IUMSCompletionList;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IUMSCompletionList::GetUnblockNotifications 方法](../Topic/IUMSCompletionList::GetUnblockNotifications%20Method.md)|擷取代表執行內容的 `IUMSUnblockNotification` 介面鏈結，自從上一次叫用此方法後，已解除其相關執行緒 Proxy。|  
  
## 備註  
 對於使用此介面清除完成清單中的項目後應執行哪些動作，排程器必須相當謹慎。  項目應該放在可執行內容的排程器的清單上，而且通常可以盡快存取。  自佇列清除的項目可以被授與任意鎖定的擁有權。  呼叫清除佇列項目和將這些項目放置於通常可在排程器內存取的清單上之間，排程器不能進行可能封鎖的任意函式呼叫。  
  
## 繼承階層架構  
 `IUMSCompletionList`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 結構](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSUnblockNotification 結構](../../../parallel/concrt/reference/iumsunblocknotification-structure.md)