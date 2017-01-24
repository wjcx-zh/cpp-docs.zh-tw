---
title: "IUMSThreadProxy 結構 | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSThreadProxy 結構"
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSThreadProxy 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

執行緒的抽象概念。  如果您想要授與使用者模式可排程的 \(UMS\) 給您的執行緒，請將排程器原則項目  `SchedulerKind` 的值設為 `UmsThreadDefault`，並實作 `IUMSScheduler` 介面。  只有安裝 Windows 7 \(含以上\) 版本的 64 位元作業系統支援 UMS 執行緒。  
  
## 語法  
  
```  
struct IUMSThreadProxy : public IThreadProxy;  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|說明|  
|--------|--------|  
|[IUMSThreadProxy::EnterCriticalRegion 方法](../Topic/IUMSThreadProxy::EnterCriticalRegion%20Method.md)|呼叫以輸入關鍵區域。  在關鍵區域內，排程器不會觀察在該區域期間發生的非同步封鎖作業。  這表示 UMS 執行緒不會因分頁錯誤、執行緒暫止、核心非同步程序呼叫 \(APC\) 等而重新進入排程器。|  
|[IUMSThreadProxy::EnterHyperCriticalRegion 方法](../Topic/IUMSThreadProxy::EnterHyperCriticalRegion%20Method.md)|呼叫以輸入超關鍵區域。  在超關鍵區域內，排程器不會觀察區域期間發生任何封鎖作業。  這表示 UMS 執行緒不會因封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 \(APC\) 等而重新進入排程器。|  
|[IUMSThreadProxy::ExitCriticalRegion 方法](../Topic/IUMSThreadProxy::ExitCriticalRegion%20Method.md)|呼叫以離開關鍵區域。|  
|[IUMSThreadProxy::ExitHyperCriticalRegion 方法](../Topic/IUMSThreadProxy::ExitHyperCriticalRegion%20Method.md)|呼叫以離開超關鍵區域。|  
|[IUMSThreadProxy::GetCriticalRegionType 方法](../Topic/IUMSThreadProxy::GetCriticalRegionType%20Method.md)|傳回執行緒 Proxy 所在的關鍵區域類型。  由於超關鍵區域是關鍵區域的超集，如果程式碼已進入關鍵區域，然後超關鍵區域，將會傳回 `InsideHyperCriticalRegion`。|  
  
## 繼承階層  
 [IThreadProxy](../../../parallel/concrt/reference/ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## 需求  
 **標頭：** concrtrm.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 結構](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [SchedulerType 列舉](../Topic/SchedulerType%20Enumeration.md)