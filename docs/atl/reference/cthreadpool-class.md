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
- ATL.CThreadPool
- ATL::CThreadPool
- CThreadPool
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 632514d03e7037ef42a1566462db5dec6f5cc1e5
ms.lasthandoff: 02/24/2017

---
# <a name="cthreadpool-class"></a>CThreadPool 類別
這個類別會提供處理工作項目的佇列的背景工作執行緒集區。  
  
## <a name="syntax"></a>語法  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>參數  
 *背景工作*  
 符合類別[工作者原型](../../atl/reference/worker-archetype.md)提供用於處理的工作項目加入佇列的執行緒集區的程式碼。  
  
 `ThreadTraits`  
 類別，提供用於建立執行緒集區中的函式。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|執行緒集區的建構函式。|  
|[CThreadPool:: ~ CThreadPool](#dtor)|執行緒集區的解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|實作`IUnknown::AddRef`。|  
|[CThreadPool::GetNumThreads](#getnumthreads)|呼叫這個方法來取得集區中的執行緒數目。|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|呼叫這個方法來取得 IO 完成連接埠，用來佇列工作項目控制代碼。|  
|[CThreadPool::GetSize](#getsize)|呼叫這個方法來取得集區中的執行緒數目。|  
|[CThreadPool::GetTimeout](#gettimeout)|呼叫這個方法，以毫秒為單位，執行緒集區會等待關閉執行緒取得的最長時間。|  
|[CThreadPool::Initialize](#initialize)|呼叫這個方法來初始化執行緒集區。|  
|[CThreadPool::QueryInterface](#queryinterface)|實作**Iid**。|  
|[CThreadPool::QueueRequest](#queuerequest)|呼叫這個方法來處理執行緒集區中的工作項目佇列。|  
|[CThreadPool::Release](#release)|實作`IUnknown::Release`。|  
|[CThreadPool::SetSize](#setsize)|呼叫此方法以設定集區中的執行緒數目。|  
|[CThreadPool::SetTimeout](#settimeout)|呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。|  
|[CThreadPool::Shutdown](#shutdown)|呼叫這個方法，以關閉執行緒集區。|  
  
## <a name="remarks"></a>備註  
 執行緒集區中的建立和終結時初始化、 調整大小時，或關閉集區。 類別的執行個體*工作者*將建立的集區中每個背景工作執行緒堆疊上。 每個執行個體將會即時執行緒的存留期。  
  
 建立的執行緒之後立即,*工作者*::`Initialize`與該執行緒相關聯的物件時呼叫。 之前的執行緒，解構*工作者*::`Terminate`將呼叫。 這兩種方法必須接受**void\* **引數。 此引數的值會傳遞到執行緒集區`pvWorkerParam`參數[CThreadPool::Initialize](#initialize)。  
  
 當有可用的工作項目佇列和背景工作執行緒中的工作時，背景工作執行緒會提取的項目關閉的佇列和呼叫**Execute**方法*工作者*該執行緒的物件。 三個項目接著會傳遞至方法︰ 從相同佇列的項目`pvWorkerParam`傳遞至*工作者*::`Initialize`和*背景工作*:: `Terminate`，及指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342) IO 完成連接埠佇列所用的結構。  
  
 *工作者*類別宣告的項目都會排入執行緒集區所提供的 typedef，型別*工作者*:: `RequestType`。 這個型別必須能夠在轉型**ULONG_PTR**。  
  
 舉例來說，*工作者*類別是[CNonStatelessWorker 類別](../../atl/reference/cnonstatelessworker-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="a-nameaddrefa--cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef  
 實作`IUnknown::AddRef`。  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 1。  
  
### <a name="remarks"></a>備註  
 這個類別不會實作使用參考計數的存留期控制項。  
  
##  <a name="a-namecthreadpoola--cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool  
 執行緒集區的建構函式。  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化逾時值[ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10)。  
  
##  <a name="a-namedtora--cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 執行緒集區的解構函式。  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[CThreadPool::Shutdown](#shutdown)。  
  
##  <a name="a-namegetnumthreadsa--cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回集區中的執行緒數目。  
  
##  <a name="a-namegetqueuehandlea--cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 呼叫這個方法來取得 IO 完成連接埠，用來佇列工作項目控制代碼。  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果尚未初始化執行緒集區會傳回佇列控制代碼則為 NULL。  
  
##  <a name="a-namegetsizea--cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize  
 呼叫這個方法來取得集區中的執行緒數目。  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>參數  
 `pnNumThreads`  
 [out]接收的變數，成功時，執行緒數目的集區中的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-namegettimeouta--cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout  
 呼叫這個方法，以毫秒為單位，執行緒集區會等待關閉執行緒取得的最長時間。  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>參數  
 `pdwMaxWait`  
 [out]接收的變數，成功時，最長的時間以毫秒為單位，執行緒集區會等待執行緒關閉的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個逾時值由[CThreadPool::Shutdown](#shutdown)如果沒有其他的值提供給該方法。  
  
##  <a name="a-nameinitializea--cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Initialize  
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
 背景工作參數，傳遞至背景工作執行緒物件`Initialize`， **Execute**，和`Terminate`方法。  
  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)將乘以取得的執行緒總數機器的處理器數目。  
  
 `dwStackSize`  
 每個執行緒集區中的堆疊大小。  
  
 *hCompletion*  
 要完成連接埠相關聯的物件控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-namequeryinterfacea--cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface  
 實作**Iid**。  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>備註  
 這個類別的物件可以成功地查詢**IUnknown**和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)介面。  
  
##  <a name="a-namequeuerequesta--cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest  
 呼叫這個方法來處理執行緒集區中的工作項目佇列。  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>參數  
 `request`  
 要排入佇列的要求。  
  
### <a name="return-value"></a>傳回值  
 成功時，會傳回 TRUE 失敗，則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法會將工作項目加入佇列。 執行緒集區中的選取項目從佇列接收它們的順序。  
  
##  <a name="a-namereleasea--cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Release  
 實作`IUnknown::Release`。  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 1。  
  
### <a name="remarks"></a>備註  
 這個類別不會實作使用參考計數的存留期控制項。  
  
##  <a name="a-namesetsizea--cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize  
 呼叫此方法以設定集區中的執行緒數目。  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>參數  
 `nNumThreads`  
 執行緒集區中的要求的數目。  
  
 如果`nNumThreads`是負數，其絕對值將會乘以取得的執行緒總數機器的處理器數目。  
  
 如果`nNumThreads`為零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)將乘以取得的執行緒總數機器的處理器數目。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 如果指定的執行緒數目小於目前的集區中的執行緒數目，物件會關閉訊息佇列來挑選所等候的執行緒。 當等候的執行緒中提取佇列訊息時，它會通知執行緒集區，並結束執行緒的程序。 此程序會重複，直到執行緒集區中的數目到達指定的數目或所指定的期間內沒有執行緒結束[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情況下，方法會傳回對應到 HRESULT **WAIT_TIMEOUT**並取消暫止的關閉訊息。  
  
##  <a name="a-namesettimeouta--cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout  
 呼叫這個方法來設定以毫秒為單位，執行緒集區會等待執行緒關閉的時間上限。  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區會等待執行緒關閉要求的最大時間。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 在逾時，會初始化為[ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10)建構函式。  
  
 請注意，`dwMaxWait`是集區會等待單一執行緒關閉的時間。 移除集區中的多個執行緒可以採取的最大時間可能會稍微小於`dwMaxWait`乘以執行緒數目。  
  
##  <a name="a-nameshutdowna--cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Shutdown  
 呼叫這個方法，以關閉執行緒集區。  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwMaxWait`  
 以毫秒為單位，執行緒集區會等待執行緒關閉要求的最大時間。 如果有提供 0 或沒有值，這個方法會使用設定的逾時[CThreadPool::SetTimeout](#settimeout)。  
  
### <a name="remarks"></a>備註  
 這個方法會張貼關機要求的所有執行緒集區中。 如果在逾時到期時，這個方法會呼叫[TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717)任何未結束的執行緒。 類別的解構函式會自動呼叫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [IThreadPoolConfig 介面](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [類別](../../atl/reference/atl-classes.md)

