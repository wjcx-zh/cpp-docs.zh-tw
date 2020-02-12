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
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139966"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 結構

執行緒的抽象概念。 如果您想要將可使用者模式排程 (UMS) 的執行緒授與給排程器，請將排程器原則項目 `SchedulerKind` 的值設為 `UmsThreadDefault`，並實作 `IUMSScheduler` 介面。 只有安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。

## <a name="syntax"></a>語法

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IUMSThreadProxy：： EnterCriticalRegion](#entercriticalregion)|呼叫以輸入重要區域。 在重要區域內時，排程器將不會觀察在區域期間發生的非同步封鎖作業。 這表示不會針對 UMS 執行緒，重新輸入排程器的分頁錯誤、執行緒暫停、核心非同步程序呼叫（Apc）等等。|
|[IUMSThreadProxy：： EnterHyperCriticalRegion](#enterhypercriticalregion)|呼叫以輸入超關鍵區域。 在超關鍵區域內時，排程器不會觀察在區域期間發生的任何封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。|
|[IUMSThreadProxy：： ExitCriticalRegion](#exitcriticalregion)|呼叫以結束重要區域。|
|[IUMSThreadProxy：： ExitHyperCriticalRegion](#exithypercriticalregion)|呼叫以結束超關鍵區域。|
|[IUMSThreadProxy：： GetCriticalRegionType](#getcriticalregiontype)|傳回執行緒 proxy 在哪種重要區域。 因為超關鍵區域是重要區域的超集合，所以如果程式碼輸入了重要區域，然後是超關鍵區域，則會傳回 `InsideHyperCriticalRegion`。|

## <a name="inheritance-hierarchy"></a>繼承階層

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="entercriticalregion"></a>IUMSThreadProxy：： EnterCriticalRegion 方法

呼叫以輸入重要區域。 在重要區域內時，排程器將不會觀察在區域期間發生的非同步封鎖作業。 這表示不會針對 UMS 執行緒，重新輸入排程器的分頁錯誤、執行緒暫停、核心非同步程序呼叫（Apc）等等。

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

重要區域的新深度。 關鍵區域是可重新進入的。

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy：： EnterHyperCriticalRegion 方法

呼叫以輸入超關鍵區域。 在超關鍵區域內時，排程器不會觀察在區域期間發生的任何封鎖作業。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超關鍵區域的新深度。 超關鍵區域是可重新進入的。

### <a name="remarks"></a>備註

排程器必須特別小心它所呼叫的方法，以及它在這類區域中所取得的鎖定。 如果這類區域中的程式碼封鎖了排程器負責排程的某個專案所持有的鎖定，則可能會控制發生鎖死。

## <a name="exitcriticalregion"></a>IUMSThreadProxy：： ExitCriticalRegion 方法

呼叫以結束重要區域。

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

重要區域的新深度。 關鍵區域是可重新進入的。

## <a name="exithypercriticalregion"></a>IUMSThreadProxy：： ExitHyperCriticalRegion 方法

呼叫以結束超關鍵區域。

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超關鍵區域的新深度。 超關鍵區域是可重新進入的。

## <a name="getcriticalregiontype"></a>IUMSThreadProxy：： GetCriticalRegionType 方法

傳回執行緒 proxy 在哪種重要區域。 因為超關鍵區域是重要區域的超集合，所以如果程式碼輸入了重要區域，然後是超關鍵區域，則會傳回 `InsideHyperCriticalRegion`。

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>傳回值

執行緒 proxy 所在的重要區欄位型別。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)
