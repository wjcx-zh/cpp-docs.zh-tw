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
ms.openlocfilehash: 0b970915aa07fe2d1af2b3a07345d5b19826be69
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330573"
---
# <a name="cthreadpool-class"></a>CThreadPool 類別

此類提供處理工作項佇列的工作線程池。

## <a name="syntax"></a>語法

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>參數

*工人*<br/>
類符合[輔助角色原型](../../atl/reference/worker-archetype.md),提供用於處理線程池上排隊的工作項的代碼。

*執行緒特徵*<br/>
提供用於在池中創建線程的函數的類。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CThreadPool:CThreadPool](#cthreadpool)|線程池的構造函數。|
|[CThreadPool:*CThreadPool](#dtor)|線程池的析構函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CThreadPool::添加參考](#addref)|`IUnknown::AddRef` 的實作。|
|[CThreadPool:取得線程](#getnumthreads)|調用此方法獲取池中的線程數。|
|[CThreadPool:取得QueueHandle](#getqueuehandle)|呼叫此方法取得用於對工作項進行排隊的 IO 完成連接埠的句柄。|
|[CThreadPool:取得 Size](#getsize)|調用此方法獲取池中的線程數。|
|[CThreadPool:取得超時](#gettimeout)|調用此方法,獲取線程池將等待線程關閉的最大時間(以毫秒為單位)。|
|[CThreadPool:初始化](#initialize)|調用此方法以初始化線程池。|
|[CThreadPool:查詢介面](#queryinterface)|`IUnknown::QueryInterface` 的實作。|
|[CThreadPool:佇列請求](#queuerequest)|調用此方法以對池中的線程要處理的工作項進行排隊。|
|[CThreadPool:發佈](#release)|`IUnknown::Release` 的實作。|
|[CThreadPool:設定大小](#setsize)|調用此方法以設置池中的線程數。|
|[CThreadPool:設置超時](#settimeout)|調用此方法以設置線程池將等待線程關閉的最大時間(以毫秒為單位)。|
|[CThreadPool:關閉](#shutdown)|調用此方法以關閉線程池。|

## <a name="remarks"></a>備註

在初始化、調整大小或關閉池時,將創建和銷毀池中的線程。 將在池中每個輔助線程的堆疊上創建類*輔助角色*實例。 每個實例將活在線程的生存期內。

建立線程後,將立即呼叫與該緒關聯的`Initialize`物件上的*輔助角色*:: 。 在銷毀線程之前,將立即呼叫*輔助角色*`Terminate`:: 。 這兩種方法都必須接受**void**<strong>\*</strong>參數。 此參數的值透過 CThreadPool 的*pvWorkerParam*參數傳遞給線程池[::初始化](#initialize)。

當佇列中的工作項和工作線程中可用於工作時,工作線程將從佇列中拉出一個項,並調用該線程`Execute`*的輔助物件*的方法。 然後,三個項傳遞給方法:佇列中的項,相同的`pvWorkerParam`傳遞給*輔助角色*`Initialize`:: 和`Terminate`*輔助角色*:: , 以及指向 IO 完成埠佇列的[OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)結構的指標。

Worker 類透過`RequestType`提供 typedef、Worker:: , 聲明將線上程池上排隊的*Worker**Worker*項目的類型。 此類型必須能夠強制轉換到ULONG_PTR。

*輔助工*類別的範例是[「無狀態輔助角色」 類別](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IUnknown`

[IThreadPool 設定](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::添加參考

`IUnknown::AddRef` 的實作。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>傳回值

始終返回 1。

### <a name="remarks"></a>備註

此類不使用引用計數實現存留期控制。

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool:CThreadPool

線程池的構造函數。

```
CThreadPool() throw();
```

### <a name="remarks"></a>備註

將超時值初始化為ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默認時間是 36 秒。 如有必要,您可以在包含 atlutil.h 之前為此符號定義您自己的正整數值。

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool:*CThreadPool

線程池的析構函數。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>備註

呼叫[CThreadPool:: 關閉](#shutdown)。

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool:取得線程

調用此方法獲取池中的線程數。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>傳回值

返回池中的線程數。

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool:取得QueueHandle

呼叫此方法取得用於對工作項進行排隊的 IO 完成連接埠的句柄。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>傳回值

如果線程池尚未初始化,則返回佇列句柄或 NULL。

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool:取得 Size

調用此方法獲取池中的線程數。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>參數

*pnNumThreads*<br/>
[出]變數的位址,在成功時,接收池中的線程數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool:取得超時

調用此方法,獲取線程池將等待線程關閉的最大時間(以毫秒為單位)。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>參數

*pdwMaxWait*<br/>
[出]變數的位址,在成功時,接收線程池將等待線程關閉的最大時間(以毫秒為單位)。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[CThreadPool::](#shutdown)如果未向該方法提供其他值,則使用此超時值::如果未向該方法提供其他值,則關閉。

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool:初始化

調用此方法以初始化線程池。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>參數

*pvWorkerParam*<br/>
要傳遞給輔助線程物件的`Initialize`輔助角色`Execute`參數 ,`Terminate`和方法。

*nNumThreads*<br/>
池中請求的線程數。

如果*nNumThreads*為負值,則其絕對值將乘以電腦中的處理器數,以獲得線程總數。

如果*nNumThreads*為零,ATLS_DEFAULT_THREADSPERPROC將乘以計算機中的處理器數,以獲得線程總數。  默認值為每處理器 2 個線程。 如有必要,您可以在包含 atlutil.h 之前為此符號定義您自己的正整數值。

*dwStackSize*<br/>
池中每個線程的堆疊大小。

*h 完成*<br/>
要與完成埠關聯的物件的句柄。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool:查詢介面

`IUnknown::QueryInterface` 的實作。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>備註

可以成功查詢此類的物件`IUnknown`和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)介面。

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool:佇列請求

調用此方法以對池中的線程要處理的工作項進行排隊。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>參數

*要求*<br/>
要排隊的請求。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此方法將工作項添加到佇列中。 池中的線程按接收項的順序從佇列中選取項。

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool:發佈

`IUnknown::Release` 的實作。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>傳回值

始終返回 1。

### <a name="remarks"></a>備註

此類不使用引用計數實現存留期控制。

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool:設定大小

調用此方法以設置池中的線程數。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>參數

*nNumThreads*<br/>
池中請求的線程數。

如果*nNumThreads*為負值,則其絕對值將乘以電腦中的處理器數,以獲得線程總數。

如果*nNumThreads*為零,ATLS_DEFAULT_THREADSPERPROC將乘以計算機中的處理器數,以獲得線程總數。 默認值為每處理器 2 個線程。 如有必要,您可以在包含 atlutil.h 之前為此符號定義您自己的正整數值。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

如果指定的線程數小於池中當前線程數,則物件將在佇列中放置一條關機消息,以便等待線程選取。 當等待的線程將消息從佇列中拉出時,它會通知線程池並退出線程過程。 此過程將重複,直到池中的線程數達到指定數量,或者直到[GetTimeout](#gettimeout)/ [設置超時](#settimeout)指定的期間沒有線程退出。 在此情況下,該方法將返回一個對應於WAIT_TIMEOUT的 HRESULT,並且掛起的關機消息將被取消。

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool:設置超時

調用此方法以設置線程池將等待線程關閉的最大時間(以毫秒為單位)。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
請求的最大時間(以毫秒為單位)用於線程池將等待線程關閉。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

超時初始化為ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默認時間是 36 秒。 如有必要,您可以在包含 atlutil.h 之前為此符號定義您自己的正整數值。

請注意 *,dwMaxWait*是池將等待單個線程關閉的時間。 從池中刪除多個線程所可能需要的最大時間可能略低於*dwMaxWait*乘以線程數。

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool:關閉

調用此方法以關閉線程池。

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*<br/>
請求的最大時間(以毫秒為單位)用於線程池將等待線程關閉。 如果提供 0 或沒有值,此方法將使用[CThreadPool::SetTimeout](#settimeout)設置的超時設置。

### <a name="remarks"></a>備註

此方法將關機請求發佈到池中的所有線程。 如果超時過期,此方法將在未退出的任何線程上調用[TerminateThread。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) 此方法從類的析構函數自動調用。

## <a name="see-also"></a>另請參閱

[IThreadPool 設定介面](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[預設執行緒特徵](atl-typedefs.md#defaultthreadtraits)<br/>
[類別](../../atl/reference/atl-classes.md)
