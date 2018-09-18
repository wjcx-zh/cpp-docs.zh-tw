---
title: IExecutionResource 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9704fc4340d52a32be4571d4cb6f4a7f8af4b67e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026942"
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
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|傳回已啟動的虛擬處理器數目根目錄，並訂閱目前與這個執行資源表示基礎硬體執行緒相關聯的外部執行緒。|  
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|傳回表示這個執行資源的硬體執行緒的唯一識別碼。|  
|[IExecutionResource::GetNodeId](#getnodeid)|傳回這個執行資源所屬的 [處理器] 節點的唯一識別碼。|  
|[IExecutionResource::Remove](#remove)|傳回這個執行資源至 Resource Manager。|  
  
## <a name="remarks"></a>備註  
 執行資源可以是獨立或與虛擬處理器根相關聯。 在您的應用程式中的執行緒會建立執行緒的訂用帳戶時，會建立獨立的執行資源。 方法[ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread)並[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)建立執行緒的訂用帳戶，並傳回`IExecutionResource`介面代表訂用帳戶。 建立執行緒的訂用帳戶是通知資源管理員之給定的執行緒要參與工作的方式已排入佇列到排程器，以及 Resource Manager 會將指派給排程器的虛擬處理器根。 Resource Manager 使用的資訊以避免超載使用硬體執行緒，它可以在這裡。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IExecutionResource`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="currentsubscriptionlevel"></a>  Iexecutionresource:: Currentsubscriptionlevel 方法  
 傳回已啟動的虛擬處理器數目根目錄，並訂閱目前與這個執行資源表示基礎硬體執行緒相關聯的外部執行緒。  
  
```
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前的訂用帳戶層級。  
  
### <a name="remarks"></a>備註  
 訂用帳戶層級會告訴您執行的執行緒數目會與硬體執行緒相關聯。 這只會包含資源管理員不知道的訂閱的執行緒] 和 [正在執行的執行緒 proxy 虛擬處理器根形式的執行緒。  
  
 呼叫方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)，或方法[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)參數`doSubscribeCurrentThread`設值`true`硬體執行緒的訂用帳戶層級遞增一。 它們也會傳回`IExecutionResource`介面代表訂用帳戶。 對應呼叫[iexecutionresource:: Remove](#remove)遞減一個硬體執行緒的訂用帳戶層級。  
  
 啟動虛擬處理器根，使用方法的 act [ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)硬體執行緒的訂用帳戶層級遞增一。 方法[ivirtualprocessorroot:: Deactivate](ivirtualprocessorroot-structure.md#deactivate)，或[iexecutionresource:: Remove](#remove)減一時啟動的虛擬處理器根上叫用的訂用帳戶層級。  
  
 Resource Manager 使用的訂用帳戶層級資訊做為其中一個決定何時要排程器之間移動資源的方式。  
  
##  <a name="getexecutionresourceid"></a>  Iexecutionresource:: Getexecutionresourceid 方法  
 傳回表示這個執行資源的硬體執行緒的唯一識別碼。  
  
```
virtual unsigned int GetExecutionResourceId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 這個執行資源的基礎硬體執行緒的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 每個硬體執行緒並行執行階段指派唯一的識別碼。 如果有多個執行資源相關聯的硬體執行緒，它們會都相同的執行資源識別碼。  
  
##  <a name="getnodeid"></a>  Iexecutionresource:: Getnodeid 方法  
 傳回這個執行資源所屬的 [處理器] 節點的唯一識別碼。  
  
```
virtual unsigned int GetNodeId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 處理器節點唯一識別碼。  
  
### <a name="remarks"></a>備註  
 並行執行階段代表處理器節點群組中的系統上的硬體執行緒數目。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都屬於相同處理器節點。 Resource Manager 會將唯一識別碼指派給這些節點從開始`0`最多且含`nodeCount - 1`，其中`nodeCount`表示系統上的處理器節點總數。  
  
 可以從函數中取得的節點計數[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
##  <a name="remove"></a>  Iexecutionresource:: Remove 方法  
 傳回這個執行資源至 Resource Manager。  
  
```
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```  
  
### <a name="parameters"></a>參數  
*pScheduler*<br/>
若要移除這個執行資源要求的排程器介面。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法傳回獨立執行的資源，以及與虛擬處理器根，資源管理員相關聯的執行資源。  
  
 如果這是獨立執行資源您收到來自其中一種方法[ischedulerproxy:: Subscribecurrentthread](ischedulerproxy-structure.md#subscribecurrentthread)或是[ischedulerproxy:: Requestinitialvirtualprocessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors)，則呼叫方法`Remove`會結束該資源已建立的執行緒訂用帳戶代表。 您不需要結束關機排程器 proxy 之前, 的所有執行緒的訂用帳戶，然後必須呼叫`Remove`從建立訂用帳戶的執行緒。  
  
 虛擬處理器根同樣可以透過叫用 `Remove` 方法傳回至資源管理員，因為介面 `IVirtualProcessorRoot` 繼承自 `IExecutionResource` 介面。 您可能需要呼叫回應中傳回虛擬處理器根[ischeduler:: Removevirtualprocessors](ischeduler-structure.md#removevirtualprocessors)方法，或當您完成從您取得過度的虛擬處理器根[Ischedulerproxy:: Createoversubscriber](ischedulerproxy-structure.md#createoversubscriber)方法。 虛擬處理器根，沒有任何限制在哪一個執行緒上叫用`Remove`方法。  
  
 `invalid_argument` 如果擲回參數`pScheduler`設為`NULL`。  
  
 `invalid_operation` 如果擲回參數`pScheduler`是不同於這個執行資源已建立的或以獨立執行資源，排程器，如果目前的執行緒不同於建立執行緒的訂用帳戶的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)
