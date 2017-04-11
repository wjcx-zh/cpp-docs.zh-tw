---
title: "CThreadPool 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: b3c944958ba73240131fba33db95dbc20ec9bec8
ms.lasthandoff: 03/31/2017

---
# <a name="cthreadpool-class"></a>CThreadPool 類別
這個類別會提供處理的工作項目佇列的背景工作執行緒集區。  
  
## <a name="syntax"></a>語法  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>參數  
 *背景工作*  
 類別不符合[工作者原型](../../atl/reference/worker-archetype.md)提供用於處理的工作項目加入執行緒集區佇列的程式碼。  
  
 `ThreadTraits`  
 提供用來建立執行緒集區中的函數類別。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|執行緒集區的建構函式。|  
|[CThreadPool:: ~ CThreadPool](#dtor)|執行緒集區的解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|實作`IUnknown::AddRef`。|  
|[CThreadPool::GetNumThreads](#getnumthreads)|呼叫這個方法來取得集區中的執行緒數目。|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|呼叫這個方法來取得用來佇列工作項目 IO 完成連接埠控制代碼。|  
|[CThreadPool::GetSize](#getsize)|呼叫這個方法來取得集區中的執行緒數目。|  
|[CThreadPool::GetTimeout](#gettimeout)|呼叫這個方法，以毫秒為單位，執行緒集區將會等到關閉執行緒取得最大時間。|  
|[CThreadPool::Initialize](#initialize)|呼叫這個方法來初始化執行緒集區。|  
|[CThreadPool::QueryInterface](#queryinterface)|實作**iunknown:: Queryinterface**。|  
|[CThreadPool::QueueRequest](#queuerequest)|呼叫此方法以處理執行緒集區中的工作項目排入佇列。|  
|[CThreadPool::Release](#release)|實作`IUnknown::Release`。|  
|[CThreadPool::SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|  
|[CThreadPool::SetTimeout](#settimeout)|呼叫此方法以設定以毫秒為單位，執行緒集區關閉執行緒的等候時間上限。|  
|[CThreadPool::Shutdown](#shutdown)|呼叫這個方法，以關閉執行緒集區。|  
  
## <a name="remarks"></a>備註  
 執行緒集區中的建立和終結時初始化、 調整大小，或關閉在集區。 類別的執行個體*工作者*將建立的集區中每個工作者執行緒堆疊上。 每個執行個體將會即時為執行緒的存留期間。  
  
 建立的執行緒之後立即,*工作者*::`Initialize`將與該執行緒相關聯的物件上呼叫。 之前的執行緒，解構*工作者*::`Terminate`將呼叫。 這兩種方法必須接受**void\***引數。 此引數的值會傳遞到執行緒集區，以透過`pvWorkerParam`參數[CThreadPool::Initialize](#initialize)。  
  
 工作項目中的佇列和背景工作執行緒可用時的工作，背景工作執行緒將會提取項目關閉的佇列和呼叫**Execute**方法*工作者*該執行緒的物件。 三個項目接著會傳遞至方法︰ 從相同佇列的項目`pvWorkerParam`傳遞至*工作者*::`Initialize`和*工作者*:: `Terminate`，以及一個指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) IO 完成連接埠佇列所用的結構。  
  
 *工作者*類別宣告的類型，將所提供的 typedef，執行緒集區佇列的項目*工作者*:: `RequestType`。 此類型必須是能夠要轉換的**ULONG_PTR**。  
  
 舉例來說，*工作者*類別是[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="addref"></a>CThreadPool::AddRef  
 實作`IUnknown::AddRef`。  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一定會傳回 1。  
  
### <a name="remarks"></a>備註  
 此類別未實作使用參考計數的存留期控制項。  
  
##  <a name="cthreadpool"></a>CThreadPool::CThreadPool  
 執行緒集區的建構函式。  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化逾時值`ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`。 預設時間為 36 秒。 如有必要，您可以再包含 atlutil.h 定義您自己的正整數值，這個符號。  
  
##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 執行緒集區的解構函式。  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[CThreadPool::Shutdown](#shutdown)。  
  
##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回集區中的執行緒數目。  
  
##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 呼叫這個方法來取得用來佇列工作項目 IO 完成連接埠控制代碼。  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果尚未初始化執行緒集區會傳回佇列控制代碼或 NULL。  
  
##  <a name="getsize"></a>CThreadPool::GetSize  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>參數  
 `pnNumThreads`  
 [out]此變數會在成功時，接收的執行緒數目位址集區中的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="gettimeout"></a>CThreadPool::GetTimeout  
 呼叫這個方法，以毫秒為單位，執行緒集區將會等到關閉執行緒取得最大時間。  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>參數  
 `pdwMaxWait`  
 [out]位址之變數的成功時，收到的最長時間的執行緒集區會關閉執行緒等候的毫秒數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個逾時值由[CThreadPool::Shutdown](#shutdown)如果沒有其他的值提供給該方法。  
  
##  <a name="initialize"></a>CThreadPool::Initialize  
 呼叫這個方法來初始化執行緒集區。  
  
```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `pvWorkerParam`  
 要傳遞給背景工作執行緒物件的背景工作參數`Initialize`， **Execute**，和`Terminate`方法。  
  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零，`ATLS_DEFAULT_THREADSPERPROC`將會乘以取得的執行緒總數機器的處理器數目。  預設值為 2 個執行緒每個處理器。 如有必要，您可以再包含 atlutil.h 定義您自己的正整數值，這個符號。
  
 `dwStackSize`  
 每個執行緒集區中的堆疊大小。  
  
 *hCompletion*  
 要完成通訊埠與建立關聯物件的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="queryinterface"></a>CThreadPool::QueryInterface  
 實作**iunknown:: Queryinterface**。  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>備註  
 這個類別的物件可以成功地查詢**IUnknown**和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)介面。  
  
##  <a name="queuerequest"></a>CThreadPool::QueueRequest  
 呼叫此方法以處理執行緒集區中的工作項目排入佇列。  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>參數  
 `request`  
 要排入佇列的要求。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會將工作項目加入至佇列。 執行緒集區中的挑選關閉佇列的項目已接收的順序。  
  
##  <a name="release"></a>CThreadPool::Release  
 實作`IUnknown::Release`。  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一定會傳回 1。  
  
### <a name="remarks"></a>備註  
 此類別未實作使用參考計數的存留期控制項。  
  
##  <a name="setsize"></a>CThreadPool::SetSize  
 呼叫此方法以設定集區中的執行緒數目。  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>參數  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零，`ATLS_DEFAULT_THREADSPERPROC`將會乘以取得的執行緒總數機器的處理器數目。 預設值為 2 個執行緒每個處理器。 如有必要，您可以再包含 atlutil.h 定義您自己的正整數值，這個符號。
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 如果指定的執行緒數目小於目前的集區中的執行緒數目，物件會關閉訊息佇列，以便收取的等候執行緒。 當等候執行緒會提取關閉佇列的訊息時，它會通知執行緒集區，並會結束執行緒的程序。 此程序會重複，直到集區中的執行緒數目達到指定的數目或沒有執行緒已結束所指定的期間內[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情況下則方法會傳回 HRESULT 對應的**WAIT_TIMEOUT**並取消暫止的關閉訊息。  
  
##  <a name="settimeout"></a>CThreadPool::SetTimeout  
 呼叫此方法以設定以毫秒為單位，執行緒集區關閉執行緒的等候時間上限。  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區將會等到關閉執行緒要求的最大時間。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 在逾時初始化為`ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`。 預設時間為 36 秒。 如有必要，您可以再包含 atlutil.h 定義您自己的正整數值，這個符號。 
  
 請注意，`dwMaxWait`是在集區將等候單一執行緒關閉的時間。 可以採取移除集區中的多個執行緒的最大時間可能稍微小於`dwMaxWait`乘以執行緒數目。  
  
##  <a name="shutdown"></a>CThreadPool::Shutdown  
 呼叫這個方法，以關閉執行緒集區。  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區將會等到關閉執行緒要求的最大時間。 如果提供 0 或沒有值，這個方法會使用設定的逾時[CThreadPool::SetTimeout](#settimeout)。  
  
### <a name="remarks"></a>備註  
 這個方法會公佈關機要求的所有執行緒集區中。 如果在逾時到期時，會呼叫這個方法[TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717)任何未結束的執行緒。 從類別的解構函式自動呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [類別](../../atl/reference/atl-classes.md)

