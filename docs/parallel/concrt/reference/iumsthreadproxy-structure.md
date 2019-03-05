---
title: IUMSThreadProxy 結構
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: 258f249aa178b73da2080cca888409dc07f63dbb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263026"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 結構

執行緒的抽象概念。 如果您想要將可使用者模式排程 (UMS) 的執行緒授與給排程器，請將排程器原則項目 `SchedulerKind` 的值設為 `UmsThreadDefault`，並實作 `IUMSScheduler` 介面。 只有安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。

## <a name="syntax"></a>語法

```
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSThreadProxy::EnterCriticalRegion](#entercriticalregion)|呼叫以輸入關鍵區域。 在關鍵區域內的排程器不會發現非同步區域可能發生的封鎖作業。 這表示，排程器將不會重新輸入為分頁錯誤、 執行緒暫止、 核心非同步程序呼叫 (Apc) 等，UMS 執行緒。|
|[IUMSThreadProxy::EnterHyperCriticalRegion](#enterhypercriticalregion)|呼叫以輸入超關鍵區域。 在超關鍵區域內的排程器不會發現任何區域可能發生的封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。|
|[IUMSThreadProxy::ExitCriticalRegion](#exitcriticalregion)|呼叫以結束關鍵區域。|
|[IUMSThreadProxy::ExitHyperCriticalRegion](#exithypercriticalregion)|呼叫以結束超關鍵區域。|
|[IUMSThreadProxy::GetCriticalRegionType](#getcriticalregiontype)|傳回何種執行緒 proxy 會在關鍵區域。 因為超關鍵區域是關鍵區域的超集，如果程式碼已進入關鍵區域，然後超關鍵區域，`InsideHyperCriticalRegion`會傳回。|

## <a name="inheritance-hierarchy"></a>繼承階層

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="entercriticalregion"></a>  Iumsthreadproxy:: Entercriticalregion 方法

呼叫以輸入關鍵區域。 在關鍵區域內的排程器不會發現非同步區域可能發生的封鎖作業。 這表示，排程器將不會重新輸入為分頁錯誤、 執行緒暫止、 核心非同步程序呼叫 (Apc) 等，UMS 執行緒。

```
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

關鍵區域的新的深度。 關鍵區域是可重新進入。

##  <a name="enterhypercriticalregion"></a>  Iumsthreadproxy:: Enterhypercriticalregion 方法

呼叫以輸入超關鍵區域。 在超關鍵區域內的排程器不會發現任何區域可能發生的封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。

```
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超關鍵區域的新的深度。 Hyper-v 關鍵區域是可重新進入。

### <a name="remarks"></a>備註

排程器必須小心富含有關其所呼叫的方法和其鎖定取得這類區域中，項目。 如果這類區域中的程式碼區塊由排程器會負責排程保留的鎖定，可能會發生死結。

##  <a name="exitcriticalregion"></a>  Iumsthreadproxy:: Exitcriticalregion 方法

呼叫以結束關鍵區域。

```
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

關鍵區域的新的深度。 關鍵區域是可重新進入。

##  <a name="exithypercriticalregion"></a>  Iumsthreadproxy:: Exithypercriticalregion 方法

呼叫以結束超關鍵區域。

```
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超關鍵區域的新的深度。 Hyper-v 關鍵區域是可重新進入。

##  <a name="getcriticalregiontype"></a>  Iumsthreadproxy:: Getcriticalregiontype 方法

傳回何種執行緒 proxy 會在關鍵區域。 因為超關鍵區域是關鍵區域的超集，如果程式碼已進入關鍵區域，然後超關鍵區域，`InsideHyperCriticalRegion`會傳回。

```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>傳回值

關鍵區域內的執行緒 proxy 是型別。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)
