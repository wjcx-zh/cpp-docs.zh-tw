---
title: "內容類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
dev_langs:
- C++
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: fd6f59e1e94329ef73e8fdbe946ec22241815e2e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="context-class"></a>Context 類別
代表執行內容的抽象概念。  
  
## <a name="syntax"></a>語法  
  
```
class Context;
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[~ Context 解構函式](#dtor)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[區塊](#block)|封鎖目前的內容。|  
|[CurrentContext](#currentcontext)|傳回目前內容的指標。|  
|[GetId](#getid)|傳回的內容，內容所屬的排程器內必須是唯一的識別碼。|  
|[GetScheduleGroupId](#getschedulegroupid)|傳回內容目前正在使用排程群組的識別碼。|  
|[GetVirtualProcessorId](#getvirtualprocessorid)|傳回內容目前正在執行的虛擬處理器的識別碼。|  
|[識別碼](#id)|傳回目前內容中目前的內容所屬的排程器的唯一識別碼。|  
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|指示傳回工作集合目前正在執行內嵌於目前的內容是在使用中的取消 （或將會在短時間內）。|  
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|判斷同步遭到封鎖的內容。 內容會被視為應用程式明確執行造成封鎖的動作會以同步方式封鎖。|  
|[過度訂閱](#oversubscribe)|插入排程器的額外的虛擬處理器的一段程式碼的其中一個該排程器中的虛擬處理器上執行的內容上叫用時持續期間。|  
|[ScheduleGroupId](#schedulegroupid)|傳回目前內容是使用排程群組的識別碼。|  
|[解除封鎖](#unblock)|解除封鎖內容，並使其成為可執行。|  
|[VirtualProcessorId](#virtualprocessorid)|傳回目前內容上執行之虛擬處理器的識別碼。|  
|[產生](#yield)|會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。|  
  
## <a name="remarks"></a>備註  
 並行執行階段排程器 (請參閱[排程器](scheduler-class.md)) 會使用執行內容來執行工作排入佇列，您的應用程式。 Win32 執行緒是 Windows 作業系統上執行內容的範例。  
  
 在任何時間，排程器的並行處理等級相當於授與資源管理員的虛擬處理器數目。 虛擬處理器是抽象的處理序的資源和對應至基礎系統的硬體執行緒。 虛擬處理器可以執行單一排程器內容在指定的時間。  
  
 排程器是合作性質，也就是希望進入等候狀態的執行內容在任何時間產生不同的內容及其虛擬處理器。 當它符合等待時，它無法繼續，直到可用的虛擬處理器，從排程器開始執行它。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `Context`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="block"></a>區塊 

 封鎖目前的內容。  
  
```
static void __cdecl Block();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
 如果虛擬處理器上執行時呼叫的內容，虛擬處理器會找到另一個可執行的內容執行，或可能會建立一個新。  
  
 之後`Block`方法被呼叫，或將呼叫中，您必須將它搭配呼叫[解除封鎖](#unblock)方法，從另一個執行內容中執行一次。 請注意，您的程式碼發行另一個執行緒可以呼叫其內容的點之間是關鍵時間`Unblock`方法和點的實際方法呼叫來`Block`為止。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 呼叫`Block`和`Unblock`方法不會追蹤封鎖和解除封鎖的原因。 只有一個物件應有的擁有權`Block` -  `Unblock`配對。  
  
 這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。  
  
##  <a name="dtor"></a>~ 內容 

```
virtual ~Context();
```  
  
##  <a name="currentcontext"></a>CurrentContext 

 傳回目前內容的指標。  
  
```
static Context* __cdecl CurrentContext();
```  
  
### <a name="return-value"></a>傳回值  
 目前內容的指標。  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
##  <a name="getid"></a>GetId 

 傳回的內容，內容所屬的排程器內必須是唯一的識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 內容所屬的排程器內必須是唯一的內容識別項。  
  
##  <a name="getschedulegroupid"></a>GetScheduleGroupId 

 傳回內容目前正在使用排程群組的識別碼。  
  
```
virtual unsigned int GetScheduleGroupId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 目前正在使用排程群組內容的識別碼。  
  
### <a name="remarks"></a>備註  
 這個方法的傳回值是排程群組上執行內容的瞬間取樣。 如果在非目前內容的其他內容上呼叫這個方法，則值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。  
  
##  <a name="getvirtualprocessorid"></a>GetVirtualProcessorId 

 傳回內容目前正在執行的虛擬處理器的識別碼。  
  
```
virtual unsigned int GetVirtualProcessorId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 如果內容目前未執行的虛擬處理器; 目前執行內容的虛擬處理器的識別碼否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法的傳回值是某虛擬處理器上執行內容的瞬間取樣。 這個值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。  
  
##  <a name="id"></a>識別碼 

 傳回目前內容中目前的內容所屬的排程器的唯一識別碼。  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的內容會附加至排程器，針對目前的內容中目前的內容屬於哪個; 排程器的唯一識別項否則，值`-1`。  
  
##  <a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling 

 指示傳回工作集合目前正在執行內嵌於目前的內容是在使用中的取消 （或將會在短時間內）。  
  
```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```  
  
### <a name="return-value"></a>傳回值  
 如果排程器會附加至呼叫的內容，以及工作群組該內容執行內嵌工作，是否表示該工作群組是在使用中的取消 （或將會在短時間內）;否則，值`false`。  
  
##  <a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked 

 判斷同步遭到封鎖的內容。 內容會被視為應用程式明確執行造成封鎖的動作會以同步方式封鎖。  
  
```
virtual bool IsSynchronouslyBlocked() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 是否以同步方式封鎖的內容。  
  
### <a name="remarks"></a>備註  
 內容會被視為應用程式明確執行造成封鎖的動作會以同步方式封鎖。 在執行緒排程器上，這表示直接呼叫 `Context::Block` 方法或是使用 `Context::Block` 方法建置的同步處理物件。  
  
 這個方法的傳回值是瞬間是否以同步方式封鎖內容的範例。 這個值可能會過期，因而會傳回只用於在特殊情況。  
  
##  <a name="operator_delete"></a>delete 運算子 

 A`Context`由執行階段內部終結物件。 不可將它明確刪除。  
  
```
void operator delete(void* _PObject);
```  
  
### <a name="parameters"></a>參數  
 `_PObject`  
 要刪除物件的指標。  
  
##  <a name="oversubscribe"></a>過度訂閱 

 插入排程器的額外的虛擬處理器的一段程式碼的其中一個該排程器中的虛擬處理器上執行的內容上叫用時持續期間。  
  
```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```  
  
### <a name="parameters"></a>參數  
 `_BeginOversubscription`  
 如果`true`，過度訂閱期間，應該加入額外的虛擬處理器的指示。 如果`false`，表示過度訂閱應該結束，而且應該移除先前新增的虛擬處理器。  
  
##  <a name="schedulegroupid"></a>ScheduleGroupId 

 傳回目前內容是使用排程群組的識別碼。  
  
```
static unsigned int __cdecl ScheduleGroupId();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的內容會附加至排程器和排程器的識別項使用的排程群組，群組的目前內容正在進行。否則，值`-1`。  
  
##  <a name="unblock"></a>解除封鎖 

 解除封鎖內容，並使其成為可執行。  
  
```
virtual void Unblock() = 0;
```  
  
### <a name="remarks"></a>備註  
 它是完全合法的呼叫`Unblock`方法是在之前的對應呼叫[區塊](#block)方法。 只要呼叫`Block`和`Unblock`方法會正確配對、 執行階段正確地處理自然的競爭情況的其中一個排序。 `Unblock`呼叫之前進入`Block`呼叫只會取消的效果`Block`呼叫。  
  
 有數個可以從這個方法會擲回的例外狀況。 如果內容嘗試呼叫`Unblock`方法本身， [context_self_unblock](context-self-unblock-class.md)擲回例外狀況。 如果呼叫`Block`和`Unblock`未正確配對 (例如，兩個呼叫`Unblock`會針對目前執行的內容)、 [context_unblock_unbalanced](context-unblock-unbalanced-class.md)擲回例外狀況。  
  
 請注意，您的程式碼發行另一個執行緒可以呼叫其內容的點之間是關鍵時間`Unblock`方法和點的實際方法呼叫來`Block`為止。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 呼叫`Block`和`Unblock`方法不會追蹤封鎖和解除封鎖的原因。 只有一個物件應有的擁有權`Block`和`Unblock`配對。  
  
##  <a name="virtualprocessorid"></a>VirtualProcessorId 

 傳回目前內容上執行之虛擬處理器的識別碼。  
  
```
static unsigned int __cdecl VirtualProcessorId();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的內容會附加至排程器，而目前的內容; 上執行之虛擬處理器的識別碼否則，值`-1`。  
  
### <a name="remarks"></a>備註  
 這個方法的傳回值是目前的內容上執行之虛擬處理器的瞬間取樣。 這個值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。  
  
##  <a name="yield"></a>產生 

 會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。  
  
```
static void __cdecl Yield();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
##  <a name="yieldexecution"></a>YieldExecution 

 會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。  
  
```
static void __cdecl YieldExecution();
```  
  
### <a name="remarks"></a>備註  
 如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。  
  
 此函式是在新[!INCLUDE[vs_dev14](../../../ide/includes/vs_dev14_md.md)]和等同於[產生](#yield)正常運作，但是未使用 Yield 巨集在 Windows.h 中發生衝突。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)   
 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




