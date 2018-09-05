---
title: CThreadPool 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9753599f08d1e8ee238097027c501a0b56e40300
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757390"
---
# <a name="cthreadpool-class"></a>CThreadPool 類別

這個類別會提供處理的工作項目佇列的背景工作執行緒集區。

## <a name="syntax"></a>語法

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>參數

*背景工作角色*  
符合類別[背景工作原型](../../atl/reference/worker-archetype.md)提供用來處理的工作項目加入執行緒集區佇列的程式碼。

*ThreadTraits*  
提供用來建立執行緒集區中的函式類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|執行緒集區建構函式。|
|[CThreadPool:: ~ CThreadPool](#dtor)|執行緒集區的解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|實作`IUnknown::AddRef`。|
|[CThreadPool::GetNumThreads](#getnumthreads)|呼叫這個方法來取得集區中的執行緒數目。|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|呼叫這個方法來取得用來將工作項目 IO 完成連接埠的控制代碼。|
|[CThreadPool::GetSize](#getsize)|呼叫這個方法來取得集區中的執行緒數目。|
|[CThreadPool::GetTimeout](#gettimeout)|呼叫這個方法，以取得最長的時間，以毫秒為單位，執行緒集區會等待關閉執行緒。|
|[CThreadPool::Initialize](#initialize)|呼叫這個方法來初始化執行緒集區。|
|[CThreadPool::QueryInterface](#queryinterface)|實作`IUnknown::QueryInterface`。|
|[CThreadPool::QueueRequest](#queuerequest)|呼叫這個方法來處理由執行緒集區中的工作項目排入佇列。|
|[CThreadPool::Release](#release)|實作`IUnknown::Release`。|
|[CThreadPool::SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|
|[CThreadPool::SetTimeout](#settimeout)|呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。|
|[CThreadPool::Shutdown](#shutdown)|呼叫這個方法來關閉執行緒集區。|

## <a name="remarks"></a>備註

建立及終結時初始化、 調整大小，或關閉在集區執行緒集區中。 類別的執行個體*背景工作角色*將建立的集區中每個背景工作執行緒堆疊上。 每個執行個體存在之執行緒的存留期。

在往來文章，建立後立即*背景工作角色*::`Initialize`將與該執行緒相關聯的物件上呼叫。 之前的執行緒，解構*背景工作角色*::`Terminate`將呼叫。 這兩種方法必須接受**void** <strong>\*</strong>引數。 此引數的值會傳遞至執行緒集區，以透過*pvWorkerParam*的參數[CThreadPool::Initialize](#initialize)。

當有可用的工作項目中的佇列和背景工作執行緒的工作時，背景工作執行緒會提取關閉的佇列和呼叫的項目`Execute`方法*背景工作角色*該執行緒的物件。 三個項目接著會傳遞至方法： 從相同佇列的項目`pvWorkerParam`傳遞給*背景工作角色*::`Initialize`並*背景工作角色*:: `Terminate`，以及的指標[OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) IO 完成連接埠佇列所用的結構。

*背景工作角色*類別會宣告都會排入執行緒集區所提供的 typedef，項目的類型*工作者*:: `RequestType`。 此類型必須能夠從 ULONG_PTR 來回轉換。

舉例*背景工作角色*類別是[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>需求

**標頭：** atlutil.h

##  <a name="addref"></a>  CThreadPool::AddRef

實作`IUnknown::AddRef`。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>傳回值

一律會傳回 1。

### <a name="remarks"></a>備註

此類別未實作使用參考計數的存留期控制項。

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

執行緒集區建構函式。

```
CThreadPool() throw();
```

### <a name="remarks"></a>備註

初始化以 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT 的逾時值。 預設時間是 36 秒。 如有必要，您可以定義您自己的正整數值，這個符號包含 atlutil.h 之前。

##  <a name="dtor"></a>  CThreadPool:: ~ CThreadPool

執行緒集區的解構函式。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>備註

呼叫[CThreadPool::Shutdown](#shutdown)。

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

呼叫這個方法來取得集區中的執行緒數目。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>傳回值

傳回集區中的執行緒數目。

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

呼叫這個方法來取得用來將工作項目 IO 完成連接埠的控制代碼。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>傳回值

如果尚未初始化執行緒集區，會傳回佇列控制代碼或 NULL。

##  <a name="getsize"></a>  CThreadPool::GetSize

呼叫這個方法來取得集區中的執行緒數目。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>參數

*pnNumThreads*  
[out]成功時，執行緒數目的集區中接收變數的位址。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

呼叫這個方法，以取得最長的時間，以毫秒為單位，執行緒集區會等待關閉執行緒。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>參數

*pdwMaxWait*  
[out]變數的位址，成功時，收到的最長時間的執行緒集區會關閉執行緒等候的毫秒數。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

使用這個逾時值[CThreadPool::Shutdown](#shutdown)如果沒有其他的值提供給該方法。

##  <a name="initialize"></a>  CThreadPool::Initialize

呼叫這個方法來初始化執行緒集區。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>參數

*pvWorkerParam*  
要傳遞至背景工作執行緒物件的背景工作角色參數`Initialize`， `Execute`，和`Terminate`方法。

*nNumThreads*  
執行緒集區中的要求的數目。

如果*nNumThreads*是負數，其絕對值將會乘以中取得的執行緒總數機器的處理器數目。

如果*nNumThreads*為零，若要取得的執行緒總數機器中的處理器數目將會乘以 ATLS_DEFAULT_THREADSPERPROC。  預設為每個處理器的 2 個執行緒。 如有必要，您可以定義您自己的正整數值，這個符號包含 atlutil.h 之前。

*dwStackSize*  
集區中每個執行緒的堆疊大小。

*hCompletion*  
若要完成連接埠相關聯的物件控制代碼。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

實作`IUnknown::QueryInterface`。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>備註

這個類別的物件可以成功地查詢`IUnknown`並[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)介面。

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

呼叫這個方法來處理由執行緒集區中的工作項目排入佇列。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>參數

*要求*  
要排入佇列的要求。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

這個方法會將工作項目加入佇列。 執行緒集區中的挑選項目從佇列接收它們的順序。

##  <a name="release"></a>  CThreadPool::Release

實作`IUnknown::Release`。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>傳回值

一律會傳回 1。

### <a name="remarks"></a>備註

此類別未實作使用參考計數的存留期控制項。

##  <a name="setsize"></a>  CThreadPool::SetSize

呼叫此方法以設定集區中的執行緒數目。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>參數

*nNumThreads*  
執行緒集區中的要求的數目。

如果*nNumThreads*是負數，其絕對值將會乘以中取得的執行緒總數機器的處理器數目。

如果*nNumThreads*為零，若要取得的執行緒總數機器中的處理器數目將會乘以 ATLS_DEFAULT_THREADSPERPROC。 預設為每個處理器的 2 個執行緒。 如有必要，您可以定義您自己的正整數值，這個符號包含 atlutil.h 之前。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

如果指定的執行緒數目小於集區中目前的執行緒數目，則物件會將關閉訊息放可挑選所等候的執行緒佇列。 當等候的執行緒會提取出訊息佇列時，它會通知執行緒集區，並結束執行緒程序。 此程序會重複，直到集區中的執行緒數目達到指定的數字，或直到沒有執行緒已結束，藉由指定的期間內[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情況下，此方法會傳回 HRESULT，對應至 WAIT_TIMEOUT，並取消暫止的關閉訊息。

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*  
以毫秒為單位，執行緒集區會等待關閉執行緒要求的最大時間。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT 會初始化逾時。 預設時間是 36 秒。 如有必要，您可以定義您自己的正整數值，這個符號包含 atlutil.h 之前。

請注意， *dwMaxWait*是集區將會等候單一執行緒關閉的時間。 若要移除多個執行緒集區中，可以採取的最大時間可能是稍微少於*dwMaxWait*乘以的執行緒數目。

##  <a name="shutdown"></a>  CThreadPool::Shutdown

呼叫這個方法來關閉執行緒集區。

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>參數

*dwMaxWait*  
以毫秒為單位，執行緒集區會等待關閉執行緒要求的最大時間。 如果提供 0 或沒有值，這個方法會使用設定的逾時[CThreadPool::SetTimeout](#settimeout)。

### <a name="remarks"></a>備註

這個方法會張貼關機要求的所有執行緒集區中。 如果在逾時到期時，這個方法會呼叫[TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread)在任何未結束的執行緒。 從類別的解構函式會自動呼叫這個方法。

## <a name="see-also"></a>另請參閱

[IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)   
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
[類別](../../atl/reference/atl-classes.md)
