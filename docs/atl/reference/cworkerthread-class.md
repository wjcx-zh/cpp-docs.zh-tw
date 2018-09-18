---
title: CWorkerThread 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2c3e0eb625c492cb9f0e9a1234d33149ac201a1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040228"
---
# <a name="cworkerthread-class"></a>CWorkerThread 類別

這個類別會建立背景工作執行緒或使用現有工作區、 等候一或多個核心物件控制代碼，而且其中一個控點而收到信號時，執行指定的用戶端函式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

#### <a name="parameters"></a>參數

*ThreadTraits*<br/>
類別提供執行緒建立函式，例如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或是[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。

## <a name="members"></a>成員

### <a name="protected-structures"></a>受保護的結構

|名稱|描述|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|背景工作執行緒建構函式。|
|[CWorkerThread:: ~ CWorkerThread](#dtor)|背景工作執行緒的解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|呼叫這個方法將可等候物件的控制代碼新增至背景工作執行緒所維護的清單。|
|[CWorkerThread::AddTimer](#addtimer)|呼叫這個方法，以將定期的可等候計時器加入至背景工作執行緒所維護的清單。|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|呼叫這個方法來取得背景工作執行緒的執行緒控制代碼。|
|[CWorkerThread::GetThreadId](#getthreadid)|呼叫這個方法來取得背景工作執行緒的執行緒識別碼。|
|[CWorkerThread::Initialize](#initialize)|呼叫此方法以初始化背景工作執行緒。|
|[CWorkerThread::RemoveHandle](#removehandle)|呼叫這個方法來移除可等候物件的清單中的控制代碼。|
|[CWorkerThread::Shutdown](#shutdown)|呼叫此方法以關閉 背景工作執行緒。|

## <a name="remarks"></a>備註

### <a name="to-use-cworkerthread"></a>若要使用 CWorkerThread

1. 建立這個類別的執行個體。

2. 呼叫[CWorkerThread::Initialize](#initialize)。

3. 呼叫[CWorkerThread::AddHandle](#addhandle)與核心物件和實作之指標的控制代碼[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。

     - 或 -

     呼叫[CWorkerThread::AddTimer](#addtimer)實作之指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。

4. 實作[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)控制代碼或計時器而收到信號時採取某些動作。

5. 若要移除的可等候物件清單中的物件，請呼叫[CWorkerThread::RemoveHandle](#removehandle)。

6. 若要終止執行緒，呼叫[CWorkerThread::Shutdown](#shutdown)。

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

呼叫這個方法將可等候物件的控制代碼新增至背景工作執行緒所維護的清單。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
可等候物件的控制代碼。

*pClient*<br/>
將指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)控制代碼會收到信號時要呼叫物件上的介面。

*dwParam*<br/>
要傳遞至參數[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)控制代碼會收到信號。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)會透過呼叫*pClient*時的控制代碼*hObject*，收到信號。

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

呼叫這個方法，以將定期的可等候計時器加入至背景工作執行緒所維護的清單。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>參數

*dwInterval*<br/>
指定期間的計時器，以毫秒為單位。

*pClient*<br/>
將指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)控制代碼會收到信號時要呼叫物件上的介面。

*dwParam*<br/>
要傳遞至參數[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)控制代碼會收到信號。

*phTimer*<br/>
[out]如果成功，接收新建立的計時器的控制代碼的控制代碼變數位址。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)會透過呼叫*pClient*計時器會收到信號。

將傳遞計時器控點距離*phTimer*要[CWorkerThread::RemoveHandle](#removehandle)關閉計時器。

##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread

建構函式。

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>  CWorkerThread:: ~ CWorkerThread

解構函式。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>備註

呼叫[CWorkerThread::Shutdown](#shutdown)。

##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle

呼叫這個方法來取得背景工作執行緒的執行緒控制代碼。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>傳回值

如果尚未初始化背景工作執行緒，會傳回執行緒控制代碼或 NULL。

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

呼叫這個方法來取得背景工作執行緒的執行緒識別碼。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>傳回值

如果尚未初始化背景工作執行緒，會傳回執行緒識別碼或 NULL。

##  <a name="initialize"></a>  CWorkerThread::Initialize

呼叫此方法以初始化背景工作執行緒。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>參數

*pThread*<br/>
現有的背景工作執行緒。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

應該呼叫這個方法，來初始化物件，在建立之後，或是在呼叫之後[CWorkerThread::Shutdown](#shutdown)。

有兩個或多個`CWorkerThread`物件使用相同的背景工作執行緒，其中一個，未傳遞任何引數則會將指標傳遞至該物件初始化`Initialize`的其他方法。 使用指標初始化的物件應該關閉之前用來將它們初始化的物件。

請參閱[CWorkerThread::Shutdown](#shutdown)上初始化使用現有的物件指標時，該方法的行為如何變更的資訊。

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

呼叫這個方法來移除可等候物件的清單中的控制代碼。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
若要移除的控制代碼。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

移除控制代碼時[IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)將傳遞至相關聯物件上呼叫[AddHandle](#addhandle)。 如果這個呼叫失敗，`CWorkerThread`會呼叫 Windows [CloseHandle](https://msdn.microsoft.com/library/windows/desktop/ms724211)控制代碼上的函式。

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

呼叫此方法以關閉 背景工作執行緒。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>參數

*dwWait*<br/>
以毫秒為單位來等待背景工作執行緒關閉時間。 ATL_WORKER_THREAD_WAIT 預設為 10 秒。 如有必要，您可以定義您自己的值，這個符號包含 atlutil.h 之前。

### <a name="return-value"></a>傳回值

在成功或失敗，例如，如果發生錯誤的 HRESULT 會傳回 S_OK 的逾時值*dwWait*，超過。

### <a name="remarks"></a>備註

若要重複使用物件，呼叫[CWorkerThread::Initialize](#initialize)之後呼叫這個方法。

請注意，呼叫`Shutdown`初始化的指標，另一個物件上`CWorkerThread`物件沒有任何作用，而且一律傳回 S_OK。

## <a name="see-also"></a>另請參閱

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[類別](../../atl/reference/atl-classes.md)<br/>
[多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient 介面](../../atl/reference/iworkerthreadclient-interface.md)
