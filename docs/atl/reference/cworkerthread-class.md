---
title: "CWorkerThread 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CWorkerThread<ThreadTraits>
- ATL::CWorkerThread
- ATL.CWorkerThread
- ATL.CWorkerThread<ThreadTraits>
- CWorkerThread
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: 24
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
ms.openlocfilehash: ab1c92c1b7442025f91007ef971d81d087351212
ms.lasthandoff: 02/24/2017

---
# <a name="cworkerthread-class"></a>CWorkerThread 類別
這個類別會建立背景工作執行緒或使用現有的命名、 等候一或多個核心物件控制代碼，和其中一個控點收到信號時，執行指定的用戶端函式。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>參數  
 `ThreadTraits`  
 提供執行緒建立函式，例如類別[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。  
  
## <a name="members"></a>Members  
  
### <a name="protected-structures"></a>受保護的結構  
  
|名稱|描述|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|背景工作執行緒的建構函式。|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|背景工作執行緒的解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|呼叫這個方法將可等候物件控制代碼加入至背景工作執行緒所維護的清單。|  
|[CWorkerThread::AddTimer](#addtimer)|呼叫這個方法，以將定期可等候計時器加入至背景工作執行緒所維護的清單。|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|呼叫這個方法來取得工作者執行緒的執行緒控制代碼。|  
|[CWorkerThread::GetThreadId](#getthreadid)|呼叫這個方法來取得工作者執行緒的執行緒識別碼。|  
|[CWorkerThread::Initialize](#initialize)|呼叫此方法以初始化背景工作執行緒。|  
|[CWorkerThread::RemoveHandle](#removehandle)|呼叫此方法以移除可等候物件的清單中的控制代碼。|  
|[CWorkerThread::Shutdown](#shutdown)|呼叫這個方法，以關閉背景工作執行緒。|  
  
## <a name="remarks"></a>備註  
  
### <a name="to-use-cworkerthread"></a>若要使用 CWorkerThread  
  
1.  建立這個類別的執行個體。  
  
2.  呼叫[CWorkerThread::Initialize](#initialize)。  
  
3.  呼叫[CWorkerThread::AddHandle](#addhandle)與核心物件和變數的指標，實作的控制代碼[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
     -或-  
  
     呼叫[CWorkerThread::AddTimer](#addtimer)實作指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
4.  實作[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)時要採取某些動作時，表示控制代碼或計時器。  
  
5.  若要從可等候物件的清單中移除物件，呼叫[CWorkerThread::RemoveHandle](#removehandle)。  
  
6.  若要終止執行緒，呼叫[CWorkerThread::Shutdown](#shutdown)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlutil.h  
  
##  <a name="a-nameaddhandlea--cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle  
 呼叫這個方法將可等候物件控制代碼加入至背景工作執行緒所維護的清單。  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 可等候物件的控制代碼。  
  
 `pClient`  
 將指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的控制代碼通知時要呼叫物件上的介面。  
  
 `dwParam`  
 要傳遞至參數[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)控制代碼會收到信號。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)會透過呼叫`pClient`時控制代碼， `hObject`，收到信號。  
  
##  <a name="a-nameaddtimera--cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer  
 呼叫這個方法，以將定期可等候計時器加入至背景工作執行緒所維護的清單。  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>參數  
 *dwInterval*  
 指定計時器的週期以毫秒為單位。  
  
 `pClient`  
 將指標[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的控制代碼通知時要呼叫物件上的介面。  
  
 `dwParam`  
 要傳遞至參數[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)控制代碼會收到信號。  
  
 `phTimer`  
 [out]如果成功，接收新建立的計時器的控制代碼的控制代碼變數的位址。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)會透過呼叫`pClient`計時器會收到信號。  
  
 將傳遞計時器控點距離`phTimer`至[CWorkerThread::RemoveHandle](#removehandle)關閉計時器。  
  
##  <a name="a-namecworkerthreada--cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread  
 建構函式。  
  
```
CWorkerThread() throw();
```  
  
##  <a name="a-namedtora--cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread:: ~ CWorkerThread  
 解構函式。  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[CWorkerThread::Shutdown](#shutdown)。  
  
##  <a name="a-namegetthreadhandlea--cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle  
 呼叫這個方法來取得工作者執行緒的執行緒控制代碼。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果尚未初始化背景工作執行緒會傳回執行緒控制代碼則為 NULL。  
  
##  <a name="a-namegetthreadida--cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId  
 呼叫這個方法來取得工作者執行緒的執行緒識別碼。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果尚未初始化背景工作執行緒會傳回執行緒識別碼或 NULL。  
  
##  <a name="a-nameinitializea--cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Initialize  
 呼叫此方法以初始化背景工作執行緒。  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>參數  
 `pThread`  
 現有的背景工作執行緒。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 初始化物件，在建立之後，或是在呼叫之後，應該呼叫這個方法[CWorkerThread::Shutdown](#shutdown)。  
  
 有兩個或多個`CWorkerThread`物件使用相同的工作者執行緒，初始化未傳遞任何引數然後將指標傳遞至該物件，其中一個`Initialize`的其他方法。 使用指標初始化的物件應該關閉之前用來將它們初始化的物件。  
  
 請參閱[CWorkerThread::Shutdown](#shutdown)上使用的現有物件的指標初始化時，該方法的行為如何變更的資訊。  
  
##  <a name="a-nameremovehandlea--cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle  
 呼叫此方法以移除可等候物件的清單中的控制代碼。  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 要移除的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 移除控制代碼時[IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)將傳遞至相關聯物件上呼叫[AddHandle](#addhandle)。 如果這個呼叫失敗，`CWorkerThread`會呼叫 Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211)函式的控制碼。  
  
##  <a name="a-nameshutdowna--cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Shutdown  
 呼叫這個方法，以關閉背景工作執行緒。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwWait`  
 以毫秒為單位等待背景工作執行緒關閉的時間。  
  
### <a name="return-value"></a>傳回值  
 在成功或失敗時，例如，如果錯誤 HRESULT 會傳回 S_OK 逾時值， `dwWait`，超過。  
  
### <a name="remarks"></a>備註  
 若要重複使用該物件，呼叫[CWorkerThread::Initialize](#initialize)之後呼叫這個方法。  
  
 請注意，呼叫**關機**初始化變數的指標，另一個物件上`CWorkerThread`物件沒有任何作用，而且一定會傳回 S_OK。  
  
## <a name="see-also"></a>另請參閱  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [類別](../../atl/reference/atl-classes.md)   
 [多執行緒︰ 建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient 介面](../../atl/reference/iworkerthreadclient-interface.md)

