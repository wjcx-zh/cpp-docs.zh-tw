---
title: IUMSCompletionList 結構 |Microsoft Docs
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
ms.openlocfilehash: aabab7a127fdc072b8d3863a53c02e20139afc5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433684"
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
|[IUMSCompletionList::GetUnblockNotifications](#getunblocknotifications)|擷取一串`IUMSUnblockNotification`表示叫用其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法的執行內容的介面。|

## <a name="remarks"></a>備註

排程器必須是富含時請小心使用這個介面來清除佇列中的完成清單的項目之後執行了哪些動作。 項目應置於可執行內容的排程器的清單，並儘速可供一般存取。 很有可能其中一個清除佇列的項目具有指定任意的鎖定擁有權。 排程器可以呼叫清除佇列項目和位置的清單，通常從內存取排程器上的這些項目之間可能會封鎖任何任意的函式呼叫。

## <a name="inheritance-hierarchy"></a>繼承階層

`IUMSCompletionList`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="getunblocknotifications"></a>  Iumscompletionlist:: Getunblocknotifications 方法

擷取一串`IUMSUnblockNotification`表示叫用其相關聯的執行緒 proxy 已解除封鎖，因為上一次這個方法的執行內容的介面。

```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>傳回值

一連串的`IUMSUnblockNotification`介面。

### <a name="remarks"></a>備註

一旦重新排程的執行內容，傳回的通知是無效的。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)
