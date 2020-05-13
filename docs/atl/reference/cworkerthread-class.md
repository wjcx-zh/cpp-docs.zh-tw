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
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330214"
---
# <a name="cworkerthread-class"></a>CWorkerThread 類別

此類創建輔助線程或使用現有線程,在一個或多個內核物件句柄上等待,並在其中一個句柄發出信號時執行指定的用戶端函數。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>參數

*執行緒特徵*<br/>
提供線程建立函數的類,如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。

## <a name="members"></a>成員

### <a name="protected-structures"></a>受保護結構

|名稱|描述|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWorker 執行緒:CWorkerThread](#cworkerthread)|輔助線程的構造函數。|
|[CWorker 執行緒:*CWorkerThread](#dtor)|輔助線程的析構函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWorkerThread::添加句柄](#addhandle)|呼叫此方法以將可等待物件的句柄添加到輔助線程維護的清單。|
|[CWorkerThread::新增計時器](#addtimer)|呼叫此方法以將定期可等待計時器添加到輔助線程維護的清單。|
|[CWorker 執行緒:抓取線程句柄](#getthreadhandle)|調用此方法以獲取輔助線程的線程句柄。|
|[CWorkerThread:getThreadId](#getthreadid)|呼叫此方法以獲取輔助線程的線程 ID。|
|[CWorkerThread:初始化](#initialize)|調用此方法以初始化輔助線程。|
|[CWorkerThread::刪除句柄](#removehandle)|呼叫此方法從可等待物件清單中刪除句柄。|
|[CWorkerThread::關閉](#shutdown)|調用此方法以關閉輔助線程。|

## <a name="remarks"></a>備註

### <a name="to-use-cworkerthread"></a>使用 CWorkerThread

1. 創建此類的實例。

1. 呼叫[CWorkerThread::初始化](#initialize)。

1. 調用[CWorkerThread:使用](#addhandle)內核物件的句柄和指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)實現的指標添加 Handle。

   \- 或 -

   呼叫[CWorkerThread:使用](#addtimer)指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)實現的指標添加 Timer。

1. 實現[IWorkerThreadClient::執行](../../atl/reference/iworkerthreadclient-interface.md#execute)在發出訊號的句柄或計時器時執行一些操作。

1. 要從可等待物件清單中移除物件,請呼叫[CWorkerThread::刪除句柄](#removehandle)。

1. 要終止線程,請呼叫[CWorkerThread::關機](#shutdown)。

## <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::添加句柄

呼叫此方法以將可等待物件的句柄添加到輔助線程維護的清單。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
可等待物件的句柄。

*pClient*<br/>
指向物件上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)介面的指標,當句柄發出信號時,要調用該介面。

*德帕拉姆*<br/>
要傳遞給[IWorkerThreadClient 的參數:](../../atl/reference/iworkerthreadclient-interface.md#execute)在發出信號時執行。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[IWorkerThreadClient:當](../../atl/reference/iworkerthreadclient-interface.md#execute)句柄*hObject*發出信號時,將通過*pClient*調用執行。

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::新增計時器

呼叫此方法以將定期可等待計時器添加到輔助線程維護的清單。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>參數

*dw間隔*<br/>
指定計時器的週期(以毫秒為單位)。

*pClient*<br/>
指向物件上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)介面的指標,當句柄發出信號時,要調用該介面。

*德帕拉姆*<br/>
要傳遞給[IWorkerThreadClient 的參數:](../../atl/reference/iworkerthreadclient-interface.md#execute)在發出信號時執行。

*phTimer*<br/>
[出]HANDLE 變數的位址,在成功時,接收新創建的計時器的句柄。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

[IWorkerThreadClient:當](../../atl/reference/iworkerthreadclient-interface.md#execute)計時器發出信號時,將通過*pClient*調用執行。

將計時器句柄從*phTimer*傳遞到[CWorkerThread::刪除手柄](#removehandle)以關閉計時器。

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorker 執行緒:CWorkerThread

建構函式。

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorker 執行緒:*CWorkerThread

解構函式。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>備註

呼叫[CWorkerThread:: 關閉](#shutdown)。

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorker 執行緒:抓取線程句柄

調用此方法以獲取輔助線程的線程句柄。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>傳回值

如果工作線程尚未初始化,則返回線程句柄或 NULL。

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread:getThreadId

呼叫此方法以獲取輔助線程的線程 ID。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>傳回值

如果工作線程尚未初始化,則返回線程 ID 或 NULL。

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread:初始化

調用此方法以初始化輔助線程。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>參數

*pThread*<br/>
現有輔助線程。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

應調用此方法在創建後或調用[CWorkerThread::::關機](#shutdown)後初始化物件。

要讓兩個或多個`CWorkerThread`物件使用相同的輔助線程,請初始化其中一個物件而不傳遞任何參數,然後將指向該物件的指標傳遞給其他物件`Initialize`的方法。 使用指標初始化的物件應在用於初始化的物件之前關閉。

有關使用指向現有物件的指標初始化時該方法的行為如何變化的資訊,請參閱[CWorkerThread::關機](#shutdown)。

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::刪除句柄

呼叫此方法從可等待物件清單中刪除句柄。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>參數

*hObject*<br/>
要刪除的句柄。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

刪除句柄時[,IWorkerThreadClient::關閉處理](../../atl/reference/iworkerthreadclient-interface.md#closehandle)將在傳遞給[AddHandle](#addhandle)的關聯物件上調用。 如果此調用失敗,`CWorkerThread`將在句柄上調用 Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函數。

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::關閉

調用此方法以關閉輔助線程。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>參數

*dwWait*<br/>
等待輔助線程關閉的時間(以毫秒為單位)。 ATL_WORKER_THREAD_WAIT預設值為 10 秒。 如有必要,您可以在包含 atlutil.h 之前為此符號定義您自己的值。

### <a name="return-value"></a>傳回值

返回成功時S_OK,或失敗時出現錯誤 HRESULT,例如如果超過超時值*dwWait。*

### <a name="remarks"></a>備註

要重用該物件,請調用[CWorkerThread::](#initialize)呼叫此方法後初始化。

請注意,使用`Shutdown`指向另`CWorkerThread`一個對象的指標初始化的物件調用不起作用,並且始終返回S_OK。

## <a name="see-also"></a>另請參閱

[預設執行緒特徵](atl-typedefs.md#defaultthreadtraits)<br/>
[類別](../../atl/reference/atl-classes.md)<br/>
[多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThread用戶端介面](../../atl/reference/iworkerthreadclient-interface.md)
