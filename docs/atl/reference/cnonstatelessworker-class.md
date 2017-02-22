---
title: "CNonStatelessWorker Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CNonStatelessWorker<Worker>"
  - "ATL::CNonStatelessWorker"
  - "ATL.CNonStatelessWorker"
  - "CNonStatelessWorker"
  - "ATL::CNonStatelessWorker<Worker>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNonStatelessWorker class"
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CNonStatelessWorker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得從執行緒集區的要求並傳遞至在每個要求都會建立並終結的工作物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class Worker  
>  
class CNonStatelessWorker  
```  
  
#### 參數  
 *背景工作處理序。*  
 符合 [背景工作原型](../../atl/reference/worker-archetype.md) 的背景工作執行緒類別適用於處理要求。 [CThreadPool](../../atl/reference/cthreadpool-class.md)已佇列。  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|[CNonStatelessWorker::RequestType](../Topic/CNonStatelessWorker::RequestType.md)|[WorkerArchetype::RequestType](../Topic/WorkerArchetype::RequestType.md)的實作。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CNonStatelessWorker::Execute](../Topic/CNonStatelessWorker::Execute.md)|[WorkerArchetype::Execute](../Topic/WorkerArchetype::Execute.md)的實作。|  
|[CNonStatelessWorker::Initialize](../Topic/CNonStatelessWorker::Initialize.md)|[WorkerArchetype::Initialize](../Topic/WorkerArchetype::Initialize.md)的實作。|  
|[CNonStatelessWorker::Terminate](../Topic/CNonStatelessWorker::Terminate.md)|[WorkerArchetype::Terminate](../Topic/WorkerArchetype::Terminate.md)的實作。|  
  
## 備註  
 這個類別是簡單的背景工作執行緒 \( [CThreadPool](../../atl/reference/cthreadpool-class.md)與搭配使用。  這個類別不提供進行任何處理要求的功能。  相反地，它會執行個體化 *背景工作* 每一個要求和委派其方法的實作會傳回對該執行個體。  
  
 這個類別的優點是它提供便利的方式來變更現有的背景工作執行緒類別的狀態模型。  如果工作者類別儲存狀態，則會保留它跨多個要求，`CThreadPool` 將建立執行緒的存留期中的單一背景工作，因此，。  透過包裝在 `CNonStatelessWorker` 範本之類別 \(在使用前使用 `CThreadPool`，其保留這個背景工作和狀態的存留期 \(Lifetime\) 受限於單一要求。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)   
 [Worker Archetype](../../atl/reference/worker-archetype.md)   
 [類別](../../atl/reference/atl-classes.md)