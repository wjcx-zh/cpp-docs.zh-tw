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
ms.openlocfilehash: bdf083e2ad418269e49e53dc164f2a60f693d5d6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261384"
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 結構

代表資源管理員發出的通知，其中說明遭封鎖並觸發傳回給排程器所指派之排程內容的執行緒 Proxy 已解除鎖定，而且已準備好進行排程。 若重新排程從 `GetContext` 方法傳回之執行緒 Proxy 的相關執行內容，則此介面不正確。

## <a name="syntax"></a>語法

```
struct IUMSUnblockNotification;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSUnblockNotification::GetContext](#getcontext)|傳回`IExecutionContext`已解除封鎖執行緒 proxy 相關聯的執行內容的介面。 當這個方法會傳回，而且已重新排定的基礎執行內容，透過對呼叫`IThreadProxy::SwitchTo`方法，此介面已不再有效。|
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|傳回下一步`IUMSUnblockNotification`從方法傳回鏈結中的介面`IUMSCompletionList::GetUnblockNotifications`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`IUMSUnblockNotification`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="getcontext"></a>  Iumsunblocknotification:: Getcontext 方法

傳回`IExecutionContext`已解除封鎖執行緒 proxy 相關聯的執行內容的介面。 當這個方法會傳回，而且已重新排定的基礎執行內容，透過對呼叫`IThreadProxy::SwitchTo`方法，此介面已不再有效。

```
virtual IExecutionContext* GetContext() = 0;
```

### <a name="return-value"></a>傳回值

`IExecutionContext`已解除封鎖執行緒 proxy 的執行內容的介面。

##  <a name="getnextunblocknotification"></a>  Iumsunblocknotification:: Getnextunblocknotification 方法

傳回下一步`IUMSUnblockNotification`從方法傳回鏈結中的介面`IUMSCompletionList::GetUnblockNotifications`。

```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```

### <a name="return-value"></a>傳回值

下一步`IUMSUnblockNotification`從方法傳回鏈結中的介面`IUMSCompletionList::GetUnblockNotifications`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)
