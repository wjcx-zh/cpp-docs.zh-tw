---
title: IUMSCompletionList 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee957355510a2f62f5317d330403dc246ee8f2e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687071"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 結構
代表 UMS 完成清單。 當 UMS 執行緒封鎖時，會分派排程器的指定排程內容，以決定封鎖原始執行緒時要在基礎虛擬處理器根排程的內容。 原始執行緒解除封鎖時，作業系統會將它佇列到可透過此介面存取的完成清單中。 排程器可以在指派的排程內容或其搜尋工作的其他任何位置查詢完成清單。  
  
## <a name="syntax"></a>語法  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|擷取一連串`IUMSUnblockNotification`代表其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法叫用的執行內容的介面。|  
  
## <a name="remarks"></a>備註  
 排程器必須小心 hierarchy 之後使用這個介面來清除佇列中的完成清單項目執行哪些動作。 項目應該放在排程器的清單中的可執行的內容，並且儘速是普遍可存取。 它是鎖定的完全有可能從佇列中清除項目具有指定任意擁有權。 排程器可以進行的呼叫來清除佇列的項目與那些項目，通常可從排程器內的清單上的位置之間可能會封鎖任何任意函式呼叫。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="getunblocknotifications"></a>  Iumscompletionlist:: Getunblocknotifications 方法  
 擷取一連串`IUMSUnblockNotification`代表其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法叫用的執行內容的介面。  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 鏈結`IUMSUnblockNotification`介面。  
  
### <a name="remarks"></a>備註  
 傳回的通知之後重新排定執行內容是無效的。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IUMSScheduler 結構](iumsscheduler-structure.md)   
 [IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)
