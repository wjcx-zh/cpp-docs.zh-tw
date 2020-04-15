---
title: IExecutionContext 結構
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 532247ca1776452ad32476d2bcdfafcee3481058
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358795"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 結構

執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。

## <a name="syntax"></a>語法

```cpp
struct IExecutionContext;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 執行上下文::D](#dispatch)|線程代理開始執行特定執行上下文時調用的方法。 這應該是計劃程式的主要工作例程。|
|[I 執行內容:GetId](#getid)|返回執行上下文的唯一標識符。|
|[I 執行內容文:取得代理](#getproxy)|返回執行此上下文的線程代理的介面。|
|[I 執行內容:抓取排程](#getscheduler)|將介面返回此執行上下文所屬的計劃程式。|
|[I 執行內容:設定代理](#setproxy)|將線程代理與此執行上下文關聯。 關聯的線程代理在開始執行上下文`Dispatch`的方法之前調用此方法。|

## <a name="remarks"></a>備註

如果要實現與併發運行時的資源管理器介面的自定義計劃程式,則需要實現該`IExecutionContext`介面。 資源管理器創建的線程通過執行`IExecutionContext::Dispatch`方法代表計劃程式執行工作。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IExecutionContext`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iexecutioncontextdispatch-method"></a><a name="dispatch"></a>I 執行上下文::Dispatch 方法

線程代理開始執行特定執行上下文時調用的方法。 這應該是計劃程式的主要工作例程。

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>參數

*p 排程狀態*<br/>
指向調度此執行上下文的狀態的指標。 有關調度狀態的詳細資訊,請參閱[調整器狀態](dispatchstate-structure.md)。

## <a name="iexecutioncontextgetid-method"></a><a name="getid"></a>I 執行內容:getId 方法

返回執行上下文的唯一標識符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

唯一的整數標識符。

### <a name="remarks"></a>備註

在使用介面作為資源管理器`GetExecutionContextId`提供的方法的參數之前,應使用方法`IExecutionContext`為 實現介面的對象獲取唯一標識符。 調用`GetId`函數時,應返回相同的標識符。

從其他源獲取的標識符可能會導致未定義的行為。

## <a name="iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>I 執行內容:抓取代理方法

返回執行此上下文的線程代理的介面。

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>傳回值

`IThreadProxy` 介面。 如果執行上下文的執行緒代理未用 呼`SetProxy`叫 初始化 ,則函`NULL`數必須傳回 。

### <a name="remarks"></a>備註

資源管理員將在執行上下文中調用`SetProxy`該方法,在上下文中`IThreadProxy``Dispatch`輸入 方法之前,將介面作為參數。 無法儲存此參數, 並將呼叫`GetProxy()`時傳回到 。

## <a name="iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>I 執行內容:取得排程工具

將介面返回此執行上下文所屬的計劃程式。

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>傳回值

`IScheduler` 介面。

### <a name="remarks"></a>備註

在執行的功能使用的參數之前,`IScheduler`您需要使用有效的介面初始化執行上下文。

## <a name="iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>I 執行內容:設定代理方法

將線程代理與此執行上下文關聯。 關聯的線程代理在開始執行上下文`Dispatch`的方法之前調用此方法。

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>參數

*pThreadProxy*<br/>
即將在此執行上下文中輸入方法的`Dispatch`線程代理的介面。

### <a name="remarks"></a>備註

應保存參數`pThreadProxy`並在調`GetProxy`用 方法時將其返回。 資源管理員保證與執行上下文關聯的線程代理線上程代理執行`Dispatch`該方法時不會更改。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[IScheduler 結構](ischeduler-structure.md)<br/>
[IThreadProxy 結構](ithreadproxy-structure.md)
