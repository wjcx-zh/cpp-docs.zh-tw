---
title: "IExecutionContext 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd8b00f24970e6bbc7f582f795c26ccb96461028
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 結構
執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。  
  
## <a name="syntax"></a>語法  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IExecutionContext::Dispatch](#dispatch)|執行緒 proxy 會開始執行特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。|  
|[IExecutionContext::GetId](#getid)|傳回的執行內容的唯一識別碼。|  
|[IExecutionContext::GetProxy](#getproxy)|讓介面返回正在執行此內容的執行緒 proxy。|  
|[IExecutionContext::GetScheduler](#getscheduler)|此執行內容所屬的排程器的介面傳回。|  
|[IExecutionContext::SetProxy](#setproxy)|將執行緒 proxy 與此執行內容產生關聯。 相關聯的執行緒 proxy 在開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。|  
  
## <a name="remarks"></a>備註  
 如果您實作的介面與並行執行階段的資源管理員的自訂排程器，您必須實作`IExecutionContext`介面。 資源管理員所建立的執行緒執行工作，代表您的排程器執行`IExecutionContext::Dispatch`方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IExecutionContext`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="dispatch"></a>  Iexecutioncontext:: Dispatch 方法  
 執行緒 proxy 會開始執行特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pDispatchState`  
 在其下發送這個執行內容的狀態指標。 如需有關分派狀態的詳細資訊，請參閱[DispatchState](dispatchstate-structure.md)。  
  
##  <a name="getid"></a>  IExecutionContext::GetId Method  
 傳回的執行內容的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 的唯一整數識別碼。  
  
### <a name="remarks"></a>備註  
 您應該使用的方法`GetExecutionContextId`若要取得實作的物件的唯一識別碼`IExecutionContext`介面，您可以使用介面做為方法參數之前提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。  
  
 從不同來源取得的識別項可能會導致未定義的行為。  
  
##  <a name="getproxy"></a>  IExecutionContext::GetProxy Method  
 讓介面返回正在執行此內容的執行緒 proxy。  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IThreadProxy` 介面。 如果執行內容的執行緒 proxy 尚未初始化呼叫`SetProxy`，函式必須傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 資源管理員將會叫用`SetProxy`上執行內容，方法與`IThreadProxy`介面做為參數，再輸入`Dispatch`方法上的的內容。 您應該要儲存這個引數，並傳回呼叫`GetProxy()`。  
  
##  <a name="getscheduler"></a>  IExecutionContext::GetScheduler Method  
 此執行內容所屬的排程器的介面傳回。  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IScheduler` 介面。  
  
### <a name="remarks"></a>備註  
 您必須初始化執行內容的有效`IScheduler`再使用它做為方法參數的介面提供資源管理員。  
  
##  <a name="setproxy"></a>  IExecutionContext::SetProxy Method  
 將執行緒 proxy 與此執行內容產生關聯。 相關聯的執行緒 proxy 在開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pThreadProxy`  
 即將進入執行緒 proxy 的介面`Dispatch`上此執行內容的方法。  
  
### <a name="remarks"></a>備註  
 您應該儲存參數`pThreadProxy`並將其傳回的呼叫上`GetProxy`方法。 資源管理員 保證的執行緒 proxy 正在執行時，將不會變更執行內容相關聯的執行緒 proxy`Dispatch`方法。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)
