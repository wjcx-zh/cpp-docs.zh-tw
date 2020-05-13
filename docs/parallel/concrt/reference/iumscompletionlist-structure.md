---
title: IUMSCompletionList 結構
ms.date: 11/04/2016
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
ms.openlocfilehash: c388cc98aedbd35b2d0e00a4653a85a47abcb838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368113"
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 結構

代表 UMS 完成清單。 當 UMS 執行緒封鎖時，會分派排程器的指定排程內容，以決定封鎖原始執行緒時要在基礎虛擬處理器根排程的內容。 原始執行緒解除封鎖時，作業系統會將它佇列到可透過此介面存取的完成清單中。 排程器可以在指派的排程內容或其搜尋工作的其他任何位置查詢完成清單。

## <a name="syntax"></a>語法

```cpp
struct IUMSCompletionList;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMS 完成清單::獲取取消阻止通知](#getunblocknotifications)|檢索表示執行上下文的`IUMSUnblockNotification`介面鏈,自上次調用此方法以來,其關聯的線程代理已解除阻止。|

## <a name="remarks"></a>備註

計劃程式必須格外小心,利用此介面從完成清單中取消專案排隊後執行哪些操作。 這些專案應放在計劃程式的可運行上下文清單中,並且通常可以儘快訪問。 完全有可能,其中一個取消排隊的專案已被授予任意鎖的擁有權。 計劃程式不能進行任意的函數調用,這些調用在取消排隊項的調用和這些項放置在通常可以從計劃程式內訪問的清單中之間。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IUMSCompletionList`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iumscompletionlistgetunblocknotifications-method"></a><a name="getunblocknotifications"></a>IUMS 完成清單::獲取取消阻止通知方法

檢索表示執行上下文的`IUMSUnblockNotification`介面鏈,自上次調用此方法以來,其關聯的線程代理已解除阻止。

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>傳回值

介面鏈`IUMSUnblockNotification`。

### <a name="remarks"></a>備註

重新計劃執行上下文後,返回的通知將無效。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)
