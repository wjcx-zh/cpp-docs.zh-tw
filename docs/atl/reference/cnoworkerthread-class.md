---
title: "CNoWorkerThread 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 9d5722ece0c85c07445f22d93e4840b9188b246c
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 類別
使用此類別做為引數`MonitorClass`樣板參數，如果您想要停用動態快取維護的快取類別。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|非功能上的等同[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|  
|[CNoWorkerThread::AddTimer](#addtimer)|非功能上的等同[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|非功能上的等同[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|非功能上的等同[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|  
|[CNoWorkerThread::Initialize](#initialize)|非功能上的等同[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|非功能上的等同[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。|  
|[CNoWorkerThread::Shutdown](#shutdown)|非功能上的等同[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供相同的公用介面[CWorkerThread](../../atl/reference/cworkerthread-class.md)。 此介面必須由提供`MonitorClass`快取類別樣板參數。  
  
 此類別中的方法會實作不做任何動作。 一律會傳回 HRESULT，方法會傳回 S_OK 時，並一律傳回的控制代碼或執行緒識別碼的方法會傳回 0。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlutil.h  
  
##  <a name="addhandle"></a>CNoWorkerThread::AddHandle  
 非功能上的等同[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="addtimer"></a>CNoWorkerThread::AddTimer  
 非功能上的等同[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle  
 非功能上的等同[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>傳回值  
 永遠傳回 NULL。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="getthreadid"></a>CNoWorkerThread::GetThreadId  
 非功能上的等同[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 0。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="initialize"></a>CNoWorkerThread::Initialize  
 非功能上的等同[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="removehandle"></a>CNoWorkerThread::RemoveHandle  
 非功能上的等同[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。  
  
##  <a name="shutdown"></a>CNoWorkerThread::Shutdown  
 非功能上的等同[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>傳回值  
 一律傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 這個類別所提供的實作沒有任何作用。

