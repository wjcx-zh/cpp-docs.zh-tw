---
title: CWorkerThread 類別
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496108"
---
# <a name="cworkerthread-class"></a>CWorkerThread 類別

這個類別會建立背景工作執行緒, 或使用現有的一個或多個核心物件控制碼, 並在其中一個控制碼收到信號時, 執行指定的用戶端函式。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>參數

*ThreadTraits*<br/>
提供執行緒建立功能的類別, 例如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。

## <a name="members"></a>成員

### <a name="protected-structures"></a>受保護的結構

|名稱|說明|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|背景工作執行緒的構造函式。|
|[CWorkerThread:: ~ CWorkerThread](#dtor)|背景工作執行緒的析構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|呼叫這個方法, 將可等候物件的控制碼加入至背景工作執行緒所維護的清單。|
|[CWorkerThread::AddTimer](#addtimer)|呼叫這個方法, 將定期可等候計時器新增至背景工作執行緒所維護的清單。|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|呼叫這個方法, 以取得背景工作執行緒的執行緒控制碼。|
|[CWorkerThread::GetThreadId](#getthreadid)|呼叫這個方法, 以取得背景工作執行緒的執行緒識別碼。|
|[CWorkerThread::Initialize](#initialize)|呼叫這個方法來初始化背景工作執行緒。|
|[CWorkerThread::RemoveHandle](#removehandle)|呼叫這個方法, 從可等候物件的清單中移除控制碼。|
|[CWorkerThread::Shutdown](#shutdown)|呼叫這個方法來關閉背景工作執行緒。|

## <a name="remarks"></a>備註

### <a name="to-use-cworkerthread"></a>若要使用 CWorkerThread

1. 建立這個類別的實例。

1. 呼叫[CWorkerThread:: Initialize](#initialize)。

1. 呼叫[CWorkerThread:: AddHandle](#addhandle) , 並搭配核心物件的控制碼和[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的執行指標。

   \-或-

   呼叫[CWorkerThread:: AddTimer](#addtimer) , 並提供[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的執行指標。

1. 執行[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) , 以在控制碼或計時器收到信號時採取一些動作。

1. 若要從可等候物件清單中移除物件, 請呼叫[CWorkerThread:: RemoveHandle](#removehandle)。

1. 若要終止執行緒, 請呼叫[CWorkerThread:: Shutdown](#shutdown)。

## <a name="requirements"></a>需求

**標頭:** atlutil。h

##  <a name="addhandle"></a>CWorkerThread::AddHandle

呼叫這個方法, 將可等候物件的控制碼加入至背景工作執行緒所維護的清單。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
可等候物件的控制碼。

*pClient*<br/>
當控制碼收到信號時, 要呼叫之物件上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)介面指標。

*dwParam*<br/>
當控制碼收到信號時, 要傳遞至[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)的參數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)將會在控制碼 ( *hObject*) 收到信號時, 透過*pClient*呼叫。

##  <a name="addtimer"></a>CWorkerThread::AddTimer

呼叫這個方法, 將定期可等候計時器新增至背景工作執行緒所維護的清單。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>參數

*dwInterval*<br/>
指定計時器的期間 (以毫秒為單位)。

*pClient*<br/>
當控制碼收到信號時, 要呼叫之物件上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)介面指標。

*dwParam*<br/>
當控制碼收到信號時, 要傳遞至[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)的參數。

*phTimer*<br/>
脫銷控制碼變數的位址, 在成功時, 會接收新建立之計時器的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

當計時器收到信號時, 將會透過*pClient*呼叫[IWorkerThreadClient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) 。

將計時器控制碼從*phTimer*傳遞至[CWorkerThread:: RemoveHandle](#removehandle) , 以關閉計時器。

##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread

建構函式。

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread

解構函式。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>備註

呼叫[CWorkerThread:: Shutdown](#shutdown)。

##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

呼叫這個方法, 以取得背景工作執行緒的執行緒控制碼。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>傳回值

傳回執行緒控制碼, 如果背景工作執行緒尚未初始化, 則傳回 Null。

##  <a name="getthreadid"></a>CWorkerThread::GetThreadId

呼叫這個方法, 以取得背景工作執行緒的執行緒識別碼。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>傳回值

傳回執行緒識別碼, 如果背景工作執行緒尚未初始化, 則傳回 Null。

##  <a name="initialize"></a>CWorkerThread:: Initialize

呼叫這個方法來初始化背景工作執行緒。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>參數

*pThread*<br/>
現有的背景工作執行緒。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

在建立之後或呼叫[CWorkerThread:: Shutdown](#shutdown)之後, 應該呼叫這個方法來初始化物件。

若要讓兩個`CWorkerThread`或多個物件使用相同的背景工作執行緒, 請在不傳遞任何引數的情況下, 初始化其中`Initialize`一個, 然後將該物件的指標傳遞給其他使用者的方法。 使用指標初始化的物件應該在用來初始化它們的物件之前關閉。

如需在使用現有物件的指標初始化時, 該方法的行為如何變更的資訊, 請參閱[CWorkerThread:: Shutdown](#shutdown) 。

##  <a name="removehandle"></a>CWorkerThread::RemoveHandle

呼叫這個方法, 從可等候物件的清單中移除控制碼。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
要移除的控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

移除控制碼時, 會在傳遞至[AddHandle](#addhandle)的相關聯物件上呼叫[IWorkerThreadClient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) 。 如果這個呼叫失敗, `CWorkerThread`將會在控制碼上呼叫 Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函數。

##  <a name="shutdown"></a>CWorkerThread:: Shutdown

呼叫這個方法來關閉背景工作執行緒。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>參數

*dwWait*<br/>
等待背景工作執行緒關閉的時間 (以毫秒為單位)。 ATL_WORKER_THREAD_WAIT 預設為10秒。 如有需要, 您可以在包含 atlutil 之前, 為此符號定義您自己的值。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT, 例如, 如果超過 timeout 值*dwWait*, 則為。

### <a name="remarks"></a>備註

若要重複使用物件, 請在呼叫這個方法之後呼叫[CWorkerThread:: Initialize](#initialize) 。

請注意, `Shutdown`在以另`CWorkerThread`一個物件的指標初始化的物件上呼叫不會有任何作用, 而且一律會傳回 S_OK。

## <a name="see-also"></a>另請參閱

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[類別](../../atl/reference/atl-classes.md)<br/>
[多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient 介面](../../atl/reference/iworkerthreadclient-interface.md)
