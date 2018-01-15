---
title: "IExecutionResource 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs: C++
helpviewer_keywords: IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd22fdb38b1828e1fa86ca79b9967a546ccb9456
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iexecutionresource-structure"></a>IExecutionResource 結構
硬體執行緒的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
struct IExecutionResource;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Iexecutionresource:: Currentsubscriptionlevel](#currentsubscriptionlevel)|傳回已啟動的虛擬處理器數目根與訂閱的目前與這個執行資源所代表的基礎硬體執行緒相關聯的外部執行緒。|  
|[Iexecutionresource:: Getexecutionresourceid](#getexecutionresourceid)|傳回表示這個執行資源的硬體執行緒的唯一識別碼。|  
|[Iexecutionresource:: Getnodeid](#getnodeid)|傳回這個執行資源所屬的 [處理器] 節點的唯一識別碼。|  
|[Iexecutionresource:: Remove](#remove)|傳回這個執行資源的資源管理員。|  
  
## <a name="remarks"></a>備註  
 執行資源可以是獨立或與虛擬處理器根相關聯。 您的應用程式中的執行緒建立執行緒訂閱時，會建立獨立的執行資源。 方法[ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)和[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)建立執行緒的訂閱，並傳回`IExecutionResource`代表介面訂用帳戶。 建立執行緒的訂用帳戶是通知資源管理員工作中會參與之給定的執行緒的方式排入佇列到排程器，以及資源管理員會指派給排程器的虛擬處理器根。 資源管理員使用的資訊來避免超額使用硬體執行緒它可以在其中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IExecutionResource`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="currentsubscriptionlevel"></a>Iexecutionresource:: Currentsubscriptionlevel 方法  
 傳回已啟動的虛擬處理器數目根與訂閱的目前與這個執行資源所代表的基礎硬體執行緒相關聯的外部執行緒。  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前的訂用帳戶層級。  
  
### <a name="remarks"></a>備註  
 訂用帳戶層級會告訴您正在執行的執行緒數目會與硬體執行緒相關聯。 這只會包含的執行緒的資源管理員會注意訂閱的執行緒，以及虛擬處理器根正在執行的執行緒 proxy 的形式。  
  
 呼叫方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)，或方法[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)搭配參數`doSubscribeCurrentThread`設值`true`硬體執行緒的訂用帳戶層級遞增一。 它們也會傳回`IExecutionResource`介面代表訂用帳戶。 對應呼叫[iexecutionresource:: Remove](#remove)遞減 1 的硬體執行緒的訂用帳戶層級。  
  
 啟用虛擬處理器根，使用方法的動作[ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)硬體執行緒的訂用帳戶層級遞增一。 方法[ivirtualprocessorroot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate)，或[iexecutionresource:: Remove](#remove)一個啟動的虛擬處理器根上叫用時遞減的訂用帳戶層級。  
  
 資源管理員會使用訂用帳戶層級資訊做為其中一個，以判斷何時要移動資源排程器之間的方式。  
  
##  <a name="getexecutionresourceid"></a>Iexecutionresource:: Getexecutionresourceid 方法  
 傳回表示這個執行資源的硬體執行緒的唯一識別碼。  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 這個執行資源的基礎硬體執行緒的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 每個硬體執行緒並行執行階段指派唯一識別碼。 如果有多個執行資源相關聯的硬體執行緒，它們全部都有相同的執行資源識別碼。  
  
##  <a name="getnodeid"></a>Iexecutionresource:: Getnodeid 方法  
 傳回這個執行資源所屬的 [處理器] 節點的唯一識別碼。  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 處理器節點唯一識別碼。  
  
### <a name="remarks"></a>備註  
 並行執行階段代表硬體執行緒的處理器節點群組中的系統上。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都屬於在相同處理器節點。 資源管理員會將唯一識別項指派給這些節點從開始`0`最多並包括`nodeCount - 1`，其中`nodeCount`代表處理器在系統上的節點總數。  
  
 您可以從函式取得的節點數目[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
##  <a name="remove"></a>Iexecutionresource:: Remove 方法  
 傳回這個執行資源的資源管理員。  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pScheduler`  
 若要移除這個執行資源要求排程器介面。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法傳回獨立執行資源，以及虛擬處理器根資源管理員相關聯的執行資源。  
  
 如果這是獨立的執行資源您收到來自其中一個方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)或[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)，則呼叫方法`Remove`會結束執行緒訂用帳戶，此資源原先建立來代表。 您不需要關閉排程器 proxy、 之前結束執行緒的所有訂閱，然後必須呼叫`Remove`從建立訂用帳戶的執行緒。  
  
 虛擬處理器根同樣可以透過叫用 `Remove` 方法傳回至資源管理員，因為介面 `IVirtualProcessorRoot` 繼承自 `IExecutionResource` 介面。 您可能需要在呼叫的回應傳回虛擬處理器根[ischeduler:: Removevirtualprocessors](ischeduler-structure.md#removevirtualprocessors)方法，或當您在您取得的過度的虛擬處理器根與[Ischedulerproxy:: Createoversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法。 虛擬處理器根，沒有任何限制的執行緒上叫用`Remove`方法。  
  
 `invalid_argument`如果擲回參數`pScheduler`設`NULL`。  
  
 `invalid_operation`如果擲回參數`pScheduler`是排程器，或與獨立執行資源，建立這個執行資源的不同，如果目前的執行緒與建立執行緒的訂用帳戶的執行緒不同。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
