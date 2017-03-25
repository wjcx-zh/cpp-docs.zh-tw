---
title: "IExecutionResource 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
dev_langs:
- C++
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: 16
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: fa3c65780ac9e001e6f6b8a015dc7f70df47181f
ms.lasthandoff: 03/17/2017

---
# <a name="iexecutionresource-structure"></a>IExecutionResource 結構
硬體執行緒的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
struct IExecutionResource;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Iexecutionresource:: Currentsubscriptionlevel](#currentsubscriptionlevel)|傳回已啟動的虛擬處理器數目根目錄和訂閱目前與這個執行資源所表示的基礎硬體執行緒相關聯的外部執行緒。|  
|[Iexecutionresource:: Getexecutionresourceid](#getexecutionresourceid)|傳回表示這個執行資源的硬體執行緒的唯一識別碼。|  
|[Iexecutionresource:: Getnodeid](#getnodeid)|傳回這個執行資源所屬的處理器節點的唯一識別碼。|  
|[Iexecutionresource:: Remove](#remove)|傳回這個執行資源的資源管理員。|  
  
## <a name="remarks"></a>備註  
 執行資源可供單獨或相關聯的虛擬處理器根。 您的應用程式中的執行緒建立執行緒的訂閱時，會建立獨立執行資源。 方法[ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)和[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)建立執行緒的訂閱，並傳回`IExecutionResource`介面代表訂用帳戶。 建立執行緒訂閱就能夠通知資源管理員之給定的執行緒要參與工作排入排程器，以及資源管理員會指派給排程器的虛擬處理器根。 資源管理員使用的資訊來避免傳承硬體執行緒，它可以。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IExecutionResource`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="currentsubscriptionlevel"></a>Iexecutionresource:: Currentsubscriptionlevel 方法  
 傳回已啟動的虛擬處理器數目根目錄和訂閱目前與這個執行資源所表示的基礎硬體執行緒相關聯的外部執行緒。  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前的訂閱層級。  
  
### <a name="remarks"></a>備註  
 訂閱層級會告訴您執行的執行緒數個硬體執行緒相關聯。 這只會包含資源管理員會注意訂閱的執行緒和執行緒 proxy 正在執行的虛擬處理器根項目表單中的執行緒。  
  
 呼叫方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)，或方法[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)參數`doSubscribeCurrentThread`設定為值`true`硬體執行緒的訂閱層級遞增一。 它們也會傳回`IExecutionResource`介面代表訂用帳戶。 對應呼叫[iexecutionresource:: Remove](#remove)遞減一個硬體執行緒的訂閱層級。  
  
 啟動虛擬處理器根，使用方法的 act [ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)硬體執行緒的訂閱層級遞增一。 方法[ivirtualprocessorroot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate)，或[iexecutionresource:: Remove](#remove)遞減一個啟動的虛擬處理器根上叫用時的訂閱層級。  
  
 資源管理員會使用訂閱層級的資訊做為其中一個來判斷排程器之間移動資源的方式。  
  
##  <a name="getexecutionresourceid"></a>Iexecutionresource:: Getexecutionresourceid 方法  
 傳回表示這個執行資源的硬體執行緒的唯一識別碼。  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 這個執行資源的基礎硬體執行緒的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 每個硬體執行緒會由並行執行階段指派的唯一識別碼。 如果有多個執行資源相關聯的硬體執行緒，它們會都相同的執行資源識別碼。  
  
##  <a name="getnodeid"></a>Iexecutionresource:: Getnodeid 方法  
 傳回這個執行資源所屬的處理器節點的唯一識別碼。  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 處理器節點的唯一識別項。  
  
### <a name="remarks"></a>備註  
 並行執行階段代表硬體執行緒的處理器節點群組中的系統上。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都隸屬於相同處理器節點。 資源管理員會將唯一識別項指派給這些節點從開始`0`最多並包括`nodeCount - 1`，其中`nodeCount`代表系統上的處理器節點總數。  
  
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
 您可以使用這個方法傳回獨立執行資源，以及執行資源與資源管理員的虛擬處理器根。  
  
 這是獨立執行資源如果您收到來自其中一種方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)或[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)，呼叫方法`Remove`會結束執行緒訂閱資源之前建立來代表。 您必須排程器 proxy，在關機之前先結束執行緒的所有訂閱，且必須呼叫`Remove`從建立訂閱的執行緒。  
  
 虛擬處理器根同樣可以透過叫用 `Remove` 方法傳回至資源管理員，因為介面 `IVirtualProcessorRoot` 繼承自 `IExecutionResource` 介面。 您可能需要在呼叫的回應傳回虛擬處理器根[ischeduler:: Removevirtualprocessors](ischeduler-structure.md#removevirtualprocessors)方法，或當您完成後您取自過度的虛擬處理器根[ischedulerproxy:: Createoversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法。 虛擬處理器根，沒有任何限制在哪一個執行緒可以叫用`Remove`方法。  
  
 `invalid_argument`如果擲回參數`pScheduler`設為`NULL`。  
  
 `invalid_operation`如果擲回參數`pScheduler`是排程器，或與獨立執行資源，建立這個執行資源的不同，如果目前的執行緒不同於建立執行緒訂閱的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)

