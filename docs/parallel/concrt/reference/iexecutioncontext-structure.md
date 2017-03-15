---
title: "IExecutionContext 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IExecutionContext
dev_langs:
- C++
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 18
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 5ad3f21e55371b904ac8a597a7a66d5c5deb8339
ms.lasthandoff: 02/24/2017

---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 結構
執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。  
  
## <a name="syntax"></a>語法  
  
```
struct IExecutionContext;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Iexecutioncontext:: Dispatch 方法](#dispatch)|執行緒 proxy 會開始執行一個特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。|  
|[Iexecutioncontext:: Getid 方法](#getid)|傳回的執行內容的唯一識別碼。|  
|[Iexecutioncontext:: Getproxy 方法](#getproxy)|傳回的介面來執行此內容的執行緒 proxy。|  
|[Iexecutioncontext:: Getscheduler 方法](#getscheduler)|此執行內容所屬的排程器的介面傳回。|  
|[Iexecutioncontext:: Setproxy 方法](#setproxy)|執行緒 proxy 關聯至這個執行內容。 相關聯的執行緒 proxy 在它開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。|  
  
## <a name="remarks"></a>備註  
 如果您正在實作自訂的排程器介面與並行執行階段的資源管理員，您必須實作`IExecutionContext`介面。 資源管理員所建立的執行緒執行工作，代表您的排程器執行`IExecutionContext::Dispatch`方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IExecutionContext`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namedispatcha--iexecutioncontextdispatch-method"></a><a name="dispatch"></a>Iexecutioncontext:: Dispatch 方法  
 執行緒 proxy 會開始執行一個特定的執行內容時，會呼叫方法。 這應該是您的排程器的主工作者常式。  
  
```
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pDispatchState`  
 在發送這個執行內容的狀態指標。 如需有關分派狀態的詳細資訊，請參閱[DispatchState](dispatchstate-structure.md)。  
  
##  <a name="a-namegetida--iexecutioncontextgetid-method"></a><a name="getid"></a>Iexecutioncontext:: Getid 方法  
 傳回的執行內容的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 唯一整數識別碼。  
  
### <a name="remarks"></a>備註  
 您應該使用方法`GetExecutionContextId`取得實作之物件的唯一識別項`IExecutionContext`介面，您可以使用介面做為方法的參數之前提供資源管理員。 您應該會傳回相同的識別項時`GetId`函式會叫用。  
  
 從不同來源取得的識別項可能會導致未定義的行為。  
  
##  <a name="a-namegetproxya--iexecutioncontextgetproxy-method"></a><a name="getproxy"></a>Iexecutioncontext:: Getproxy 方法  
 傳回的介面來執行此內容的執行緒 proxy。  
  
```
virtual IThreadProxy* GetProxy() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IThreadProxy` 介面。 如果尚未初始化的執行內容的執行緒 proxy 會藉由呼叫`SetProxy`，函數必須傳回`NULL`。  
  
### <a name="remarks"></a>備註  
 資源管理員會叫用`SetProxy`上執行內容，方法與`IThreadProxy`介面做為參數，在進入之前`Dispatch`方法上的的內容。 您應該儲存此引數，並將它傳回呼叫`GetProxy()`。  
  
##  <a name="a-namegetschedulera--iexecutioncontextgetscheduler-method"></a><a name="getscheduler"></a>Iexecutioncontext:: Getscheduler 方法  
 此執行內容所屬的排程器的介面傳回。  
  
```
virtual IScheduler* GetScheduler() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 `IScheduler` 介面。  
  
### <a name="remarks"></a>備註  
 您必須初始化執行內容的有效`IScheduler`介面，再使用它做為方法的參數提供資源管理員。  
  
##  <a name="a-namesetproxya--iexecutioncontextsetproxy-method"></a><a name="setproxy"></a>Iexecutioncontext:: Setproxy 方法  
 執行緒 proxy 關聯至這個執行內容。 相關聯的執行緒 proxy 在它開始執行的內容之前，會叫用此方法的權限`Dispatch`方法。  
  
```
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pThreadProxy`  
 即將進入的執行緒 proxy 介面`Dispatch`方法，在此執行內容。  
  
### <a name="remarks"></a>備註  
 您應該儲存參數`pThreadProxy`並將它傳回呼叫`GetProxy`方法。 資源管理員可保證執行緒 proxy 正在執行時不會變更執行內容相關聯的執行緒 proxy`Dispatch`方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IScheduler 結構](ischeduler-structure.md)   
 [IThreadProxy 結構](ithreadproxy-structure.md)

