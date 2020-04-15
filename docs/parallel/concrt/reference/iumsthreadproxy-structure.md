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
ms.openlocfilehash: 2e748b1da02394e1f70afd8b92947e1291957c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368075"
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
|[IUMSThread 代理::輸入關鍵區域](#entercriticalregion)|調用以進入關鍵區域。 在關鍵區域內時,計劃程式將不會觀察到在該區域期間發生的非同步阻塞操作。 這意味著對於 UMS 線程的頁面錯誤、線程掛起、內核非同步過程調用 (APC) 等,將不會重新輸入計畫程式。|
|[IUMSThread 代理::輸入超臨界區域](#enterhypercriticalregion)|調用以進入超臨界區域。 在超臨界區域內時,計劃程式將不會觀察到該區域期間發生的任何阻塞操作。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。|
|[IUMSThread 代理::退出關鍵區域](#exitcriticalregion)|為了退出關鍵區域而調用。|
|[IUMSThread 代理::退出超臨界區域](#exithypercriticalregion)|調用以退出超關鍵區域。|
|[IUMSThread 代理::獲取臨界區域類型](#getcriticalregiontype)|返回線程代理位於哪類關鍵區域。 由於超臨界區域是關鍵區域的超集,如果代碼已進入關鍵區域,然後`InsideHyperCriticalRegion`返回一個超臨界區域。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iumsthreadproxyentercriticalregion-method"></a><a name="entercriticalregion"></a>IUMSThread 代理::輸入臨界區域方法

調用以進入關鍵區域。 在關鍵區域內時,計劃程式將不會觀察到在該區域期間發生的非同步阻塞操作。 這意味著對於 UMS 線程的頁面錯誤、線程掛起、內核非同步過程調用 (APC) 等,將不會重新輸入計畫程式。

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

關鍵區域的新深度。 關鍵區域是重入的。

## <a name="iumsthreadproxyenterhypercriticalregion-method"></a><a name="enterhypercriticalregion"></a>IUMSThread 代理::輸入超臨界區域方法

調用以進入超臨界區域。 在超臨界區域內時,計劃程式將不會觀察到該區域期間發生的任何阻塞操作。 這表示不會因為 UMS 執行緒的封鎖函式呼叫、鎖定封鎖的擷取嘗試、分頁錯誤、執行緒暫止、核心非同步程序呼叫 (APC) 等，而重新進入排程器。

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超臨界區域的新深度。 超臨界區域是重入區域。

### <a name="remarks"></a>備註

調度程序必須非常小心調用什麼方法,並在此類區域中獲取什麼鎖。 如果此類區域中的代碼阻塞了計劃程式負責計劃的內容所持有的鎖上,則可能會出現死鎖。

## <a name="iumsthreadproxyexitcriticalregion-method"></a><a name="exitcriticalregion"></a>IUMSThread 代理::退出關鍵區域方法

為了退出關鍵區域而調用。

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

關鍵區域的新深度。 關鍵區域是重入的。

## <a name="iumsthreadproxyexithypercriticalregion-method"></a><a name="exithypercriticalregion"></a>IUMSThread 代理::退出超臨界區域方法

調用以退出超關鍵區域。

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>傳回值

超臨界區域的新深度。 超臨界區域是重入區域。

## <a name="iumsthreadproxygetcriticalregiontype-method"></a><a name="getcriticalregiontype"></a>IUMSThread 代理::獲取臨界區域類型方法

返回線程代理位於哪類關鍵區域。 由於超臨界區域是關鍵區域的超集,如果代碼已進入關鍵區域,然後`InsideHyperCriticalRegion`返回一個超臨界區域。

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>傳回值

線程代理位於其中的關鍵區域的類型。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IUMSScheduler 結構](iumsscheduler-structure.md)
