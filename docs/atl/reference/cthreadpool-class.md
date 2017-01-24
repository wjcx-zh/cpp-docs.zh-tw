---
title: "CThreadPool Class | Microsoft Docs"
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
  - "ATL.CThreadPool"
  - "ATL::CThreadPool"
  - "CThreadPool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CThreadPool class"
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CThreadPool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供處理工作項目佇列的背景工作執行緒集區。  
  
## 語法  
  
```  
  
      template <  
   class Worker,  
   class ThreadTraits = DefaultThreadTraits  
>  
class CThreadPool :  
   public IThreadPoolConfig  
```  
  
#### 參數  
 *背景工作處理序。*  
 符合提供程式碼的 [背景工作原型](../../atl/reference/worker-archetype.md) 所使用的類別來處理工作項目在執行緒集區的佇列。  
  
 `ThreadTraits`  
 提供函式的類別用於建立可在集區中的執行緒。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CThreadPool::CThreadPool](../Topic/CThreadPool::CThreadPool.md)|執行緒集區的建構函式。|  
|[CThreadPool::~CThreadPool](../Topic/CThreadPool::~CThreadPool.md)|執行緒集區的解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CThreadPool::AddRef](../Topic/CThreadPool::AddRef.md)|`IUnknown::AddRef` 的實作。|  
|[CThreadPool::GetNumThreads](../Topic/CThreadPool::GetNumThreads.md)|呼叫這個方法會取得執行緒的數目在集區中。|  
|[CThreadPool::GetQueueHandle](../Topic/CThreadPool::GetQueueHandle.md)|呼叫這個方法會取得 IO 完成通訊埠的控制代碼使用至佇列的工作項目。|  
|[CThreadPool::GetSize](../Topic/CThreadPool::GetSize.md)|呼叫這個方法會取得執行緒的數目在集區中。|  
|[CThreadPool::GetTimeout](../Topic/CThreadPool::GetTimeout.md)|以毫秒為單位\) 呼叫這個方法會取得最長時間執行緒集區執行緒等待關閉。|  
|[CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md)|呼叫這個方法會初始化執行緒集區。|  
|[CThreadPool::QueryInterface](../Topic/CThreadPool::QueryInterface.md)|**IUnknown::QueryInterface**的實作。|  
|[CThreadPool::QueueRequest](../Topic/CThreadPool::QueueRequest.md)|呼叫這個方法佇列在集區的執行緒處理的工作項目。|  
|[CThreadPool::Release](../Topic/CThreadPool::Release.md)|`IUnknown::Release` 的實作。|  
|[CThreadPool::SetSize](../Topic/CThreadPool::SetSize.md)|呼叫這個方法會設定執行緒的數目在集區中。|  
|[CThreadPool::SetTimeout](../Topic/CThreadPool::SetTimeout.md)|以毫秒為單位\) 呼叫這個方法會設定最長時間執行緒集區執行緒等待關閉。|  
|[CThreadPool::Shutdown](../Topic/CThreadPool::Shutdown.md)|呼叫這個方法會關閉執行緒集區。|  
  
## 備註  
 在集區的執行緒都會建立並終結或使用時初始化，調整大小或已關閉。  類別 *背景工作* 執行個體在堆疊上建立在集區中的每個背景工作執行緒。  每個執行個體為執行緒的存留期都會填入資料。  
  
 在執行緒上建立之後， Worker::`Initialize` 將呼叫物件與該執行緒。  在執行緒的解構 Worker::`Terminate` 之前，會呼叫。  這兩個方法必須接受 **void\*** 引數。  這個引數的值傳遞給執行緒集區 [CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md)`pvWorkerParam` 參數。  
  
 發生於佇列和背景工作執行緒的工作項目中可用的工作，背景工作執行緒的拉扯項目佇列並呼叫 *工作* 物件的方法 **執行** 該執行緒的。  三個項目會傳遞給方法:從佇列、相同的 `pvWorkerParam` 傳遞至 Worker::`Initialize` 和 Worker::`Terminate`和指標的項目加入至用來 IO 完成通訊埠佇列的 [重疊。](http://msdn.microsoft.com/library/windows/desktop/ms684342) 結構。  
  
 類別宣告在 *背景工作* 執行緒集區要佇列透過提供 typedef 項目的型別， Worker::`RequestType`。  這個型別必須能夠與相互轉換 **ULONG\_PTR**。  
  
 *背景工作* 的類別範例為 [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md)。  
  
## 繼承階層架構  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [IThreadPoolConfig Interface](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [類別](../../atl/reference/atl-classes.md)