---
title: CThreadPool 類別
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 12b28cd4f54fa426bb6ad2b2710d62b426ada2b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226538"
---
# <a name="cthreadpool-class"></a>CThreadPool 類別

這個類別會提供可處理工作專案佇列的背景工作執行緒集區。

## <a name="syntax"></a>語法

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>參數

*背景工作*<br/>
類別符合背景[工作原型](../../atl/reference/worker-archetype.md)，提供用來處理線上程集區上排入佇列之工作專案的程式碼。

*ThreadTraits*<br/>
提供用來在集區中建立執行緒之函數的類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|執行緒集區的構造函式。|
|[CThreadPool：： ~ CThreadPool](#dtor)|執行緒集區的析構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CThreadPool：： AddRef](#addref)|`IUnknown::AddRef` 的實作。|
|[CThreadPool::GetNumThreads](#getnumthreads)|呼叫這個方法，以取得集區中的執行緒數目。|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|呼叫這個方法，以取得用來將工作專案排入佇列之 IO 完成通訊埠的控制碼。|
|[CThreadPool：： GetSize](#getsize)|呼叫這個方法，以取得集區中的執行緒數目。|
|[CThreadPool::GetTimeout](#gettimeout)|呼叫這個方法以取得執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。|
|[CThreadPool：： Initialize](#initialize)|呼叫這個方法來初始化執行緒集區。|
|[CThreadPool：： QueryInterface](#queryinterface)|`IUnknown::QueryInterface` 的實作。|
|[CThreadPool::QueueRequest](#queuerequest)|呼叫這個方法，將工作專案排入佇列，以便由集區中的執行緒。|
|[CThreadPool：： Release](#release)|`IUnknown::Release` 的實作。|
|[CThreadPool：： SetSize](#setsize)|呼叫這個方法，以設定集區中的執行緒數目。|
|[CThreadPool：： SetTimeout](#settimeout)|呼叫這個方法來設定執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。|
|[CThreadPool：： Shutdown](#shutdown)|呼叫這個方法來關閉執行緒集區。|

## <a name="remarks"></a>備註

當集區已初始化、調整大小或關閉時，會建立並終結集區中的執行緒。 系統會在集區中每個背景工作執行緒的堆疊上建立類別背景*工作角色*的實例。 每個實例都會線上程的存留期記憶體留。

建立執行緒之後，會立即*Worker* `Initialize` 在與該執行緒相關聯的物件上呼叫 Worker：：。 線上程的銷毀之前，會立即呼叫*Worker*：： `Terminate` 。 這兩種方法都必須接受 **`void`** <strong>\*</strong> 引數。 這個引數的值會透過[CThreadPool：： Initialize](#initialize)的*pvWorkerParam*參數傳遞至執行緒集區。

當佇列和背景工作執行緒中有工作專案可用於工作時，背景工作執行緒會從佇列提取專案，並呼叫 `Execute` 該執行緒之背景*工作*物件的方法。 然後會將三個專案傳遞至方法：佇列中的專案、 `pvWorkerParam` 傳遞給*worker*：： `Initialize` 和*worker*：： `Terminate` ，以及用於 IO 完成埠佇列之[OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)重迭結構的指標。

*Worker*類別會藉由提供 Typedef， *worker*：：，宣告將線上程集區上排入佇列的專案類型 `RequestType` 。 這個類型必須能夠在 ULONG_PTR 之間來回轉換。

背景*工作*類別的範例是[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>需求

**標頭：** atlutil。h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool：： AddRef

`IUnknown::AddRef` 的實作。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>傳回值

一律傳回1。

### <a name="remarks"></a>備註

這個類別不會使用參考計數來執行存留期控制。

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

執行緒集區的構造函式。

```
CThreadPool() throw();
```

### <a name="remarks"></a>備註

將 timeout 值初始化為 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 預設時間為36秒。 如有需要，您可以在包含 atlutil 之前，為這個符號定義您自己的正整數值。

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool：： ~ CThreadPool

執行緒集區的析構函式。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>備註

呼叫[CThreadPool：： Shutdown](#shutdown)。

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

呼叫這個方法，以取得集區中的執行緒數目。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>傳回值

傳回集區中的執行緒數目。

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

呼叫這個方法，以取得用來將工作專案排入佇列之 IO 完成通訊埠的控制碼。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>傳回值

傳回佇列控制碼，如果尚未初始化執行緒集區，則傳回 Null。

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool：： GetSize

呼叫這個方法，以取得集區中的執行緒數目。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>參數

*pnNumThreads*<br/>
脫銷在成功時，會收到集區中的執行緒數目之變數的位址。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

呼叫這個方法以取得執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>參數

*pdwMaxWait*<br/>
脫銷在成功時，變數的位址會收到執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果沒有提供其他值給該方法， [CThreadPool：： Shutdown](#shutdown)會使用這個 timeout 值。

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool：： Initialize

呼叫這個方法來初始化執行緒集區。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>參數

*pvWorkerParam*<br/>
要傳遞至背景工作執行緒物件之 `Initialize` 、和方法的背景工作參數 `Execute` `Terminate` 。

*nNumThreads*<br/>
集區中要求的執行緒數目。

如果*nNumThreads*為負數，則其絕對值會乘以電腦中的處理器數目，以取得執行緒總數。

如果*nNumThreads*為零，ATLS_DEFAULT_THREADSPERPROC 將會乘以電腦中的處理器數目，以取得執行緒總數。  預設值為每個處理器2個執行緒。 如有需要，您可以在包含 atlutil 之前，為這個符號定義您自己的正整數值。

*dwStackSize*<br/>
集區中每個執行緒的堆疊大小。

*hCompletion*<br/>
要與完成通訊埠產生關聯之物件的控制碼。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool：： QueryInterface

`IUnknown::QueryInterface` 的實作。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>備註

這個類別的物件可以成功地查詢 `IUnknown` 和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)介面。

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

呼叫這個方法，將工作專案排入佇列，以便由集區中的執行緒。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>參數

*要求*<br/>
要排入佇列的要求。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

這個方法會將工作專案加入至佇列。 集區中的執行緒會依照接收的順序來挑選佇列中的專案。

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool：： Release

`IUnknown::Release` 的實作。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>傳回值

一律傳回1。

### <a name="remarks"></a>備註

這個類別不會使用參考計數來執行存留期控制。

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool：： SetSize

呼叫這個方法，以設定集區中的執行緒數目。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>參數

*nNumThreads*<br/>
集區中要求的執行緒數目。

如果*nNumThreads*為負數，則其絕對值會乘以電腦中的處理器數目，以取得執行緒總數。

如果*nNumThreads*為零，ATLS_DEFAULT_THREADSPERPROC 將會乘以電腦中的處理器數目，以取得執行緒總數。 預設值為每個處理器2個執行緒。 如有需要，您可以在包含 atlutil 之前，為這個符號定義您自己的正整數值。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果指定的執行緒數目小於目前在集區中的執行緒數目，此物件會將關閉訊息放在佇列上，以等待中的執行緒拾取。 當等候中的執行緒從佇列中提取訊息時，它會通知執行緒集區，並結束執行緒程式。 此程式會重複執行，直到集區中的執行緒數目達到指定的數目，或直到[GetTimeout](#gettimeout)SetTimeout 所指定的期間內沒有任何執行緒結束為止 /  [ ](#settimeout)。 在這種情況下，方法會傳回對應至 WAIT_TIMEOUT 的 HRESULT，並取消暫止的關閉訊息。

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool：： SetTimeout

呼叫這個方法來設定執行緒集區等候執行緒關閉的最長時間（以毫秒為單位）。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
執行緒集區等候執行緒關閉的要求最大時間（以毫秒為單位）。

### <a name="return-value"></a>傳回值

會在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

Timeout 會初始化為 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 預設時間為36秒。 如有需要，您可以在包含 atlutil 之前，為這個符號定義您自己的正整數值。

請注意， *dwMaxWait*是集區等候單一執行緒關閉的時間。 從集區中移除多個執行緒所能採取的時間上限，可能會稍微小於*dwMaxWait*乘以執行緒數目。

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool：： Shutdown

呼叫這個方法來關閉執行緒集區。

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
執行緒集區等候執行緒關閉的要求最大時間（以毫秒為單位）。 如果0或未提供任何值，這個方法會使用[CThreadPool：： SetTimeout](#settimeout)所設定的超時時間。

### <a name="remarks"></a>備註

這個方法會將關閉要求張貼至集區中的所有線程。 如果超時時間過期，這個方法會在未結束的任何執行緒上呼叫[TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) 。 這個方法是從類別的「析構函式」自動呼叫。

## <a name="see-also"></a>另請參閱

[IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[類別](../../atl/reference/atl-classes.md)
