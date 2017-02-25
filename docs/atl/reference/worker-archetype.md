---
title: "Worker Archetype | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Worker archetype"
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# Worker Archetype
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符合 *背景工作* 原型的類別提供程式碼寫入佇列管理工作項目在執行緒集區。  
  
 **實作**  
  
 若要實作類別符合這個原型，類別必須提供下列功能:  
  
|方法|描述|  
|--------|--------|  
|[初始化](../Topic/WorkerArchetype::Initialize.md)|會在任何需要先初始化工作物件會傳遞至 [執行](../Topic/WorkerArchetype::Execute.md)。|  
|[執行](../Topic/WorkerArchetype::Execute.md)|呼叫處理工作項目。|  
|[結束](../Topic/WorkerArchetype::Terminate.md)|呼叫呼叫以取消初始化工作物件，在所有要求傳遞至 [執行](../Topic/WorkerArchetype::Execute.md)之後。|  
  
|Typedef|描述|  
|-------------|--------|  
|[RequestType](../Topic/WorkerArchetype::RequestType.md)|可由背景工作類別處理工作項目類型的 typedef。|  
  
 一般 *工作* 類別應該如下所示:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/CPP/worker-archetype_1.cpp)]  
  
 **現有實作**  
  
 這些類別符合這個原型:  
  
|類別|描述|  
|--------|--------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|取得從執行緒集區的要求並傳遞至對每個要求都會建立並終結的工作物件。|  
  
 **使用**  
  
 這些範本參數預期類別符合這個原型:  
  
|參數名稱|使用|  
|----------|--------|  
|*背景工作處理序。*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*背景工作處理序。*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [Archetypes](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)