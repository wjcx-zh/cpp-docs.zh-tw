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
ms.openlocfilehash: 0fd1ed90ca30c9c9e6815bb05b516f24b4f9a164
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513785"
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 結構

工作排程器抽象概念的介面，需要並行執行階段的資源管理員將可使用者模式排程的 (UMS) 執行緒傳遞給它。 資源管理員會使用這個介面與 UMS 執行緒排程器進行通訊。 `IUMSScheduler` 介面繼承自 `IScheduler` 介面。

## <a name="syntax"></a>語法

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|指派`IUMSCompletionList`UMS 執行緒排程器的介面。|

## <a name="remarks"></a>備註

如果您要實作自訂的排程器進行通訊與資源管理員 中，而且您想要交付給您的排程器，而不是一般 Win32 執行緒 UMS 執行緒，您應該提供實作`IUMSScheduler`介面。 此外，您應該設定的排程器原則索引鍵的原則值`SchedulerKind`要`UmsThreadDefault`。 如果原則指定 UMS 執行緒`IScheduler`介面做為參數傳遞[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法必須為`IUMSScheduler`介面。

Resource Manager 就能夠交給您只能在 UMS 功能的作業系統上的 UMS 執行緒。 Windows 7 及更新版本的 64 位元作業系統支援 UMS 執行緒。 如果您建立的排程器原則`SchedulerKind`機碼設定為值`UmsThreadDefault`和基礎平台不支援 UMS，值`SchedulerKind`機碼，該原則將會變更為值`ThreadScheduler`。 您應一律傳回這個原則值之前讀取收件者 UMS 執行緒。

`IUMSScheduler`介面是雙向的排程器與 Resource Manager 之間的通訊通道的一端。 所代表之另一端`IResourceManager`和`ISchedulerProxy`實作資源管理員的介面。

## <a name="inheritance-hierarchy"></a>繼承階層

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="setcompletionlist"></a>  Iumsscheduler:: Setcompletionlist 方法

指派`IUMSCompletionList`UMS 執行緒排程器的介面。

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>參數

*pCompletionList*<br/>
排程器完成清單介面。 沒有單一的清單，每個排程器。

### <a name="remarks"></a>備註

資源管理員會叫用指定的排程器已要求資源的初始配置之後，它會想 UMS 執行緒排程器上的這個方法。 排程器可以使用`IUMSCompletionList`介面，以判斷當 UMS 執行緒 proxy 已解除封鎖。 它只適用於從指派給 UMS 排程器的虛擬處理器根上執行的執行緒 proxy 存取這個介面。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
