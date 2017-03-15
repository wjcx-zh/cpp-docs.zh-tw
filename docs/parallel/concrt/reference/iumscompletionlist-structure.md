---
title: "IUMSCompletionList 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSCompletionList
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 25023c27244669092e0f57fe59bdb190fd2f2afb
ms.lasthandoff: 02/24/2017

---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 結構
代表 UMS 完成清單。 當 UMS 執行緒封鎖時，會分派排程器的指定排程內容，以決定封鎖原始執行緒時要在基礎虛擬處理器根排程的內容。 原始執行緒解除封鎖時，作業系統會將它佇列到可透過此介面存取的完成清單中。 排程器可以在指派的排程內容或其搜尋工作的其他任何位置查詢完成清單。  
  
## <a name="syntax"></a>語法  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Iumscompletionlist:: Getunblocknotifications 方法](#getunblocknotifications)|擷取一連串的`IUMSUnblockNotification`介面代表叫用其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法的執行內容。|  
  
## <a name="remarks"></a>備註  
 排程器必須是名符時請小心使用此介面來清除佇列中的完成清單項目之後執行了哪些動作。 項目應該放在排程器的清單中的可執行的內容，並且儘速是普遍可存取。 它是很有可能從佇列中清除的項目具有指定的任意鎖定的擁有權。 排程器可以進行的呼叫來清除佇列項目與那些項目通常能從排程器內的清單上的位置，可能會封鎖任何任意函式呼叫。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namegetunblocknotificationsa--iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>Iumscompletionlist:: Getunblocknotifications 方法  
 擷取一連串的`IUMSUnblockNotification`介面代表叫用其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法的執行內容。  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 鏈結的`IUMSUnblockNotification`介面。  
  
### <a name="remarks"></a>備註  
 傳回的通知就會重新排程的執行內容無效。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IUMSScheduler 結構](iumsscheduler-structure.md)   
 [IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)

