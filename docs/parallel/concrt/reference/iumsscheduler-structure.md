---
title: "IUMSScheduler 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs: C++
helpviewer_keywords: IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82795e3494267f953875136bb29c701c93dbc934
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 結構
工作排程器抽象概念的介面，需要並行執行階段的資源管理員將可使用者模式排程的 (UMS) 執行緒傳遞給它。 資源管理員會使用這個介面與 UMS 執行緒排程器進行通訊。 `IUMSScheduler` 介面繼承自 `IScheduler` 介面。  
  
## <a name="syntax"></a>語法  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Iumsscheduler:: Setcompletionlist](#setcompletionlist)|指派`IUMSCompletionList`UMS 執行緒排程器的介面。|  
  
## <a name="remarks"></a>備註  
 如果您要實作自訂的排程器進行通訊與資源管理員，而且您想要傳至您的排程器，而不是一般 Win32 執行緒 UMS 執行緒，您應該提供的實作`IUMSScheduler`介面。 此外，您應該設定排程器原則機碼的原則值`SchedulerKind`是`UmsThreadDefault`。 如果原則會指定 UMS 執行緒`IScheduler`傳遞為參數，以介面[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法必須為`IUMSScheduler`介面。  
  
 資源管理員都能夠把您只能在 UMS 功能的作業系統上 UMS 執行緒。 Windows 7 和更高版本的 64 位元作業系統支援 UMS 執行緒。 如果您建立的排程器原則`SchedulerKind`機值設定為`UmsThreadDefault`和基礎平台不支援的值，UMS`SchedulerKind`該原則上的金鑰將會變更為值`ThreadScheduler`。 您應一律傳回這個原則值之前讀取預期接收 UMS 執行緒。  
  
 `IUMSScheduler`介面是雙向的排程器與資源管理員之間的通訊通道的一端。 另一端由`IResourceManager`和`ISchedulerProxy`會實作資源管理員的介面。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="setcompletionlist"></a>Iumsscheduler:: Setcompletionlist 方法  
 指派`IUMSCompletionList`UMS 執行緒排程器的介面。  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pCompletionList`  
 排程器完成清單介面。 沒有單一的清單，每個排程器。  
  
### <a name="remarks"></a>備註  
 資源管理員會叫用指定的排程器已要求資源的初始配置之後，它會想 UMS 執行緒排程器上的這個方法。 排程器可以使用`IUMSCompletionList`介面，以判斷當 UMS 執行緒 proxy 已解除封鎖。 它只適用於從指派給 UMS 排程器的虛擬處理器根上執行的執行緒 proxy 存取這個介面。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IUMSCompletionList 結構](iumscompletionlist-structure.md)   
 [IResourceManager 結構](iresourcemanager-structure.md)
