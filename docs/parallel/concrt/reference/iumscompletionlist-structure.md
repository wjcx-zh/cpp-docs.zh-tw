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
ms.openlocfilehash: 02382ef4606a6e73804fcbd5ce7735ecf2f0dcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140041"
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
|[IUMSCompletionList：： GetUnblockNotifications](#getunblocknotifications)|抓取 `IUMSUnblockNotification` 介面的鏈，表示在上次叫用此方法之後，相關聯的執行緒 proxy 已解除封鎖的執行內容。|

## <a name="remarks"></a>備註

在利用此介面將完成清單中的專案清除佇列之後，排程器必須非常小心地瞭解哪些動作會執行。 這些專案應該放在排程器的可執行內容清單上，而且通常會儘快加以存取。 其中一個已清除佇列的專案，完全有可能被授與任意鎖定的擁有權。 排程器可能不會在呼叫清除佇列專案時封鎖任意函式呼叫，以及在可從排程器中一般存取的清單上放置這些專案。

## <a name="inheritance-hierarchy"></a>繼承階層

`IUMSCompletionList`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="getunblocknotifications"></a>IUMSCompletionList：： GetUnblockNotifications 方法

抓取 `IUMSUnblockNotification` 介面的鏈，表示在上次叫用此方法之後，相關聯的執行緒 proxy 已解除封鎖的執行內容。

```cpp
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```

### <a name="return-value"></a>傳回值

`IUMSUnblockNotification` 介面的鏈。

### <a name="remarks"></a>備註

重新排定執行內容之後，傳回的通知會無效。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)
