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
ms.openlocfilehash: 0b88ddd4184e982a5e07c536efc301eaa16f4a41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368064"
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
|[IUMUnSunblock 通知::獲取上下文](#getcontext)|返回與`IExecutionContext`已解除阻止的線程代理關聯的執行上下文的介面。 一旦此方法返回,並且通過調用`IThreadProxy::SwitchTo`方法 重新計劃基礎執行上下文,此介面將不再有效。|
|[IUMUnSunblock 通知::獲取下一個取消阻止通知](#getnextunblocknotification)|返回從`IUMSUnblockNotification``IUMSCompletionList::GetUnblockNotifications`方法返回的鏈中的下一個介面。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IUMSUnblockNotification`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>IUMUnSunblock 通知::獲取上下文方法

返回與`IExecutionContext`已解除阻止的線程代理關聯的執行上下文的介面。 一旦此方法返回,並且通過調用`IThreadProxy::SwitchTo`方法 重新計劃基礎執行上下文,此介面將不再有效。

```cpp
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>傳回值

執行`IExecutionContext`上下文的介面,用於已解除阻止的線程代理。

## <a name="iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>IUMUnSunblock 通知::獲取NextUnblock通知方法

返回從`IUMSUnblockNotification``IUMSCompletionList::GetUnblockNotifications`方法返回的鏈中的下一個介面。

```cpp
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>傳回值

鏈中的`IUMSUnblockNotification`下一個介面從`IUMSCompletionList::GetUnblockNotifications`方法返回。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)
