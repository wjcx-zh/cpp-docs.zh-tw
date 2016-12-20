---
title: "CNoWorkerThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CNoWorkerThread"
  - "ATL.CNoWorkerThread"
  - "CNoWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoWorkerThread class"
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNoWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您想要停用動態快取中維護，請使用這個類別做為引數才能 `MonitorClass` 樣板參數可以快取類別。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CNoWorkerThread  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CNoWorkerThread::AddHandle](../Topic/CNoWorkerThread::AddHandle.md)|[CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md)無作用的對等用法。|  
|[CNoWorkerThread::AddTimer](../Topic/CNoWorkerThread::AddTimer.md)|[CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md)無作用的對等用法。|  
|[CNoWorkerThread::GetThreadHandle](../Topic/CNoWorkerThread::GetThreadHandle.md)|[CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md)無作用的對等用法。|  
|[CNoWorkerThread::GetThreadId](../Topic/CNoWorkerThread::GetThreadId.md)|[CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md)無作用的對等用法。|  
|[CNoWorkerThread::Initialize](../Topic/CNoWorkerThread::Initialize.md)|[CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)無作用的對等用法。|  
|[CNoWorkerThread::RemoveHandle](../Topic/CNoWorkerThread::RemoveHandle.md)|[CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)無作用的對等用法。|  
|[CNoWorkerThread::Shutdown](../Topic/CNoWorkerThread::Shutdown.md)|[CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)無作用的對等用法。|  
  
## 備註  
 這個類別會提供公用介面和 [CWorkerThread](../../atl/reference/cworkerthread-class.md)相同。  這個介面必須由 `MonitorClass` 樣板參數提供給快取類別。  
  
 在這個類別中的方法將不會發生任何動作。  永遠會傳回 HRESULT 傳回 S\_OK 的和方法永遠都傳回控制代碼或執行緒 ID 的方法會傳回 0。  
  
## 需求  
 **Header:** 函式