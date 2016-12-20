---
title: "CWorkerThread Class | Microsoft Docs"
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
  - "ATL::CWorkerThread<ThreadTraits>"
  - "ATL::CWorkerThread"
  - "ATL.CWorkerThread"
  - "ATL.CWorkerThread<ThreadTraits>"
  - "CWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWorkerThread class"
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當其中一個控制代碼都收到信號時，這個類別會在一或多個核心物件控制代碼建立背景工作執行緒或使用現有的平台，等待，並執行指定的用戶端函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class ThreadTraits= DefaultThreadTraits  
>  
class CWorkerThread  
```  
  
#### 參數  
 `ThreadTraits`  
 提供執行緒建立函式，例如 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 或 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)的類別。  
  
## Members  
  
### 受保護的組態  
  
|名稱|描述|  
|--------|--------|  
|`WorkerClientEntry`||  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWorkerThread::CWorkerThread](../Topic/CWorkerThread::CWorkerThread.md)|背景工作執行緒的建構函式。|  
|[CWorkerThread::~CWorkerThread](../Topic/CWorkerThread::~CWorkerThread.md)|背景工作執行緒的解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md)|呼叫這個方法會將物件的等候控制代碼背景工作執行緒維持的清單。|  
|[CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md)|呼叫這個方法會將定期計時器等候到背景工作執行緒維持的清單。|  
|[CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md)|呼叫這個方法會取得背景工作執行緒的執行緒控制代碼。|  
|[CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md)|呼叫這個方法會取得背景工作執行緒的執行緒 ID。|  
|[CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)|呼叫這個方法會初始化背景工作執行緒。|  
|[CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)|呼叫這個方法會從清單中移除物件等候控制代碼。|  
|[CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)|呼叫這個方法會關閉背景工作執行緒。|  
  
## 備註  
  
### 使用 CWorkerThread  
  
1.  建立這個類別的執行個體。  
  
2.  呼叫 [CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)。  
  
3.  使用一個核心物件的控制代碼和指標來呼叫 [CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md) 至 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的實作。  
  
     \-或\-  
  
     會使用指標的 [CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md) 至 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的實作。  
  
4.  當這個控制代碼或計時器收到信號時，請實作 [IWorkerThreadClient::Execute](../Topic/IWorkerThreadClient::Execute.md) 採取某些動作。  
  
5.  等候物件從清單中移除物件，請呼叫 [CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)。  
  
6.  若要結束執行緒，請呼叫 [CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [類別](../../atl/reference/atl-classes.md)   
 [多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient Interface](../../atl/reference/iworkerthreadclient-interface.md)