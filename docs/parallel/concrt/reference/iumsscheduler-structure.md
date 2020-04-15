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
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368089"
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
|[IUMS計劃::設定完成清單](#setcompletionlist)|將`IUMSCompletionList`介面分配給 UMS 線程計畫程式。|

## <a name="remarks"></a>備註

如果要實現與資源管理器通信的自定義計劃程式,並且希望將 UMS 線程交給您的計畫程式而不是普通的 Win32 線程`IUMSScheduler`,則應提供 介面的實現。 此外,應將計畫程式策略鍵`SchedulerKind`的策略值設定為`UmsThreadDefault`。 如果政策指定 UMS 執行`IScheduler`緒, 則作為參數傳遞給[IResourceManager::註冊排程器](iresourcemanager-structure.md#registerscheduler)方法的`IUMSScheduler`介面必須是介面 。

資源管理員只能將 UMS 線程交給具有 UMS 功能的作業系統。 64 位元作業系統,版本 Windows 7 和更高版本支援 UMS 線程。 如果建立`SchedulerKind`設定值設定`UmsThreadDefault`為值的調度程式政策,而基礎平臺不支援 UMS,則該`SchedulerKind`策略上的 鍵的值將`ThreadScheduler`改變為值 。 在期望接收 UMS 線程之前,應始終讀取此策略值。

該`IUMSScheduler`介面是調度程式與資源管理器之間雙向通信通道的一端。 另一端由`IResourceManager`和`ISchedulerProxy`介面表示,這些介面由資源管理器實現。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[I時間](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMS計劃::設置完成清單方法

將`IUMSCompletionList`介面分配給 UMS 線程計畫程式。

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>參數

*p 完成清單*<br/>
計畫程式的完成清單介面。 每個計劃程式只有一個清單。

### <a name="remarks"></a>備註

在計劃程式請求初始分配資源後,資源管理員將在指定所需的 UMS 線程的計畫程式上調用此方法。 計劃程式可以使用介面`IUMSCompletionList`來確定 UMS 線程代理何時未解除阻止。 僅從分配給 UMS 計畫程式的虛擬處理器根上運行的線程代理訪問此介面才有效。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[策略元素鍵](concurrency-namespace-enums.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IUMSCompletionList 結構](iumscompletionlist-structure.md)<br/>
[IResourceManager 結構](iresourcemanager-structure.md)
