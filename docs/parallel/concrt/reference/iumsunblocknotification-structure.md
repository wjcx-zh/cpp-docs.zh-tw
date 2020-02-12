---
title: IUMSUnblockNotification 結構
ms.date: 11/04/2016
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
ms.openlocfilehash: d4fd95b1f11ed6edac26cb03e41e8b650acfafa3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139975"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 結構

代表資源管理員發出的通知，其中說明遭封鎖並觸發傳回給排程器所指派之排程內容的執行緒 Proxy 已解除鎖定，而且已準備好進行排程。 若重新排程從 `GetContext` 方法傳回之執行緒 Proxy 的相關執行內容，則此介面不正確。

## <a name="syntax"></a>語法

```cpp
struct IUMSUnblockNotification;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSUnblockNotification：： GetCoNtext](#getcontext)|傳回與已解除封鎖的執行緒 proxy 相關聯之執行內容的 `IExecutionContext` 介面。 一旦這個方法傳回，而且基礎執行內容已透過呼叫 `IThreadProxy::SwitchTo` 方法重新排程，這個介面就不再有效。|
|[IUMSUnblockNotification：： GetNextUnblockNotification](#getnextunblocknotification)|傳回從方法 `IUMSCompletionList::GetUnblockNotifications`傳回之鏈中的下一個 `IUMSUnblockNotification` 介面。|

## <a name="inheritance-hierarchy"></a>繼承階層

`IUMSUnblockNotification`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="getcontext"></a>IUMSUnblockNotification：： GetCoNtext 方法

傳回與已解除封鎖的執行緒 proxy 相關聯之執行內容的 `IExecutionContext` 介面。 一旦這個方法傳回，而且基礎執行內容已透過呼叫 `IThreadProxy::SwitchTo` 方法重新排程，這個介面就不再有效。

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>傳回值

對已解除封鎖的執行緒 proxy 執行內容的 `IExecutionContext` 介面。

## <a name="getnextunblocknotification"></a>IUMSUnblockNotification：： GetNextUnblockNotification 方法

傳回從方法 `IUMSCompletionList::GetUnblockNotifications`傳回之鏈中的下一個 `IUMSUnblockNotification` 介面。

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>傳回值

從方法所傳回之鏈中的下一個 `IUMSUnblockNotification` 介面 `IUMSCompletionList::GetUnblockNotifications`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)
