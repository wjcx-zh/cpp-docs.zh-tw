---
title: IUMSScheduler 結構
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139986"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 結構

工作排程器抽象概念的介面，需要並行執行階段的資源管理員將可使用者模式排程的 (UMS) 執行緒傳遞給它。 資源管理員會使用這個介面與 UMS 執行緒排程器進行通訊。 `IUMSScheduler` 介面繼承自 `IScheduler` 介面。

## <a name="syntax"></a>語法

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSScheduler：： SetCompletionList](#setcompletionlist)|將 `IUMSCompletionList` 介面指派給 UMS 執行緒排程器。|

## <a name="remarks"></a>備註

如果您要執行與 Resource Manager 通訊的自訂排程器，而且想要將 UMS 執行緒交給您的排程器，而不是一般的 Win32 執行緒，您應該提供 `IUMSScheduler` 介面的執行。 此外，您應該將排程器原則金鑰 `SchedulerKind` 的原則值設定為 `UmsThreadDefault`。 如果原則指定 UMS 執行緒，做為參數傳遞至[IResourceManager：： RegisterScheduler](iresourcemanager-structure.md#registerscheduler)方法的 `IScheduler` 介面必須是 `IUMSScheduler` 介面。

Resource Manager 只能將 UMS 執行緒交給具有 UMS 功能的作業系統。 Windows 7 和更新版本的64位作業系統支援 UMS 執行緒。 如果您建立排程器原則，並將 `SchedulerKind` 金鑰設定為值 `UmsThreadDefault` 且基礎平臺不支援 UMS，則該原則上 `SchedulerKind` 索引鍵的值將會變更為 `ThreadScheduler`的值。 在預期接收 UMS 執行緒之前，您應該一律讀回此原則值。

`IUMSScheduler` 介面是排程器與 Resource Manager 之間雙向通訊通道的一端。 另一端則是由 Resource Manager 所執行的 `IResourceManager` 和 `ISchedulerProxy` 介面所表示。

## <a name="inheritance-hierarchy"></a>繼承階層

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="setcompletionlist"></a>IUMSScheduler：： SetCompletionList 方法

將 `IUMSCompletionList` 介面指派給 UMS 執行緒排程器。

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>參數

*pCompletionList*<br/>
排程器的完成清單介面。 每個排程器都有一個清單。

### <a name="remarks"></a>備註

在排程器要求初始資源配置之後，Resource Manager 會在排程器上叫用此方法，以指定要使用 UMS 執行緒。 排程器可以使用 `IUMSCompletionList` 介面來判斷 UMS 執行緒 proxy 何時解除封鎖。 只有在指派給 UMS 排程器的虛擬處理器根上執行的執行緒 proxy 存取此介面時，才有效。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
