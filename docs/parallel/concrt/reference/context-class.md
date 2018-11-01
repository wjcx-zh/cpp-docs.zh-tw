---
title: Context 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: c6b219eabd008114f40401c64465e44607c2ee9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555073"
---
# <a name="context-class"></a>Context 類別

代表執行內容的抽象概念。

## <a name="syntax"></a>語法

```
class Context;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[~ Context 解構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[區塊](#block)|封鎖目前的內容。|
|[CurrentContext](#currentcontext)|讓指標回到目前的內容。|
|[GetId](#getid)|傳回之內容的內容所屬的排程器中的唯一識別碼。|
|[GetScheduleGroupId](#getschedulegroupid)|傳回內容目前正在使用排程群組的識別碼。|
|[GetVirtualProcessorId](#getvirtualprocessorid)|傳回虛擬處理器上目前執行內容識別碼。|
|[ID](#id)|傳回目前內容中目前的內容所屬的排程器的唯一識別碼。|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|指出是否會傳回工作集合目前正在執行內嵌於目前的內容正使用中的取消 （或會短時間內）。|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|決定以同步方式封鎖的內容。 內容會被視為是如果它已明確地執行動作，導致封鎖，以同步方式會封鎖。|
|[過度訂閱](#oversubscribe)|插入的排程器的額外的虛擬處理器的其中一個虛擬處理器，在該排程器上執行的內容上叫用時的程式碼區塊的持續時間。|
|[ScheduleGroupId](#schedulegroupid)|傳回目前的內容正在排程群組的識別碼。|
|[Unblock](#unblock)|解除封鎖的內容，並使其成為可執行。|
|[VirtualProcessorId](#virtualprocessorid)|傳回目前內容上所執行的虛擬處理器的識別碼。|
|[Yield](#yield)|會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。|

## <a name="remarks"></a>備註

並行執行階段排程器 (請參閱[排程器](scheduler-class.md)) 會使用執行內容來執行工作排入佇列，您的應用程式。 Win32 執行緒是 Windows 作業系統上執行內容的範例。

在任何時間，排程器的並行層級等於授與資源管理員的虛擬處理器數目。 虛擬處理器是處理序的資源和對應至基礎的系統上的硬體執行緒的抽象概念。 只在單一排程器的內容可以在虛擬處理器上執行，在指定的時間。

排程器是合作性質，並希望進入等候狀態的執行內容在任何時間產生不同的內容及其虛擬處理器。 等待它滿足時，它無法繼續，直到可用的虛擬處理器，從排程器開始執行。

## <a name="inheritance-hierarchy"></a>繼承階層

`Context`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="block"></a> 區塊

封鎖目前的內容。

```
static void __cdecl Block();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

如果虛擬處理器上執行呼叫的內容，虛擬處理器會發現另一個可執行的內容來執行，或可能會建立一個新。

之後`Block`方法呼叫，或將會呼叫中，您必須將它搭配呼叫[解除封鎖](#unblock)從另一個執行內容，為了讓它再次執行的方法。 注意您的程式碼發行另一個執行緒可以呼叫其內容的位置的點之間是重要的期間`Unblock`方法和點的實際方法呼叫以`Block`為止。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 若要呼叫`Block`和`Unblock`方法不會追蹤封鎖和解除封鎖的原因。 只有一個物件應具備的擁有權`Block` -  `Unblock`組。

這個方法可以擲回例外狀況，包括各種[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。

##  <a name="dtor"></a> ~ 內容

```
virtual ~Context();
```

##  <a name="currentcontext"></a> CurrentContext

讓指標回到目前的內容。

```
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>傳回值

目前內容的指標。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

##  <a name="getid"></a> GetId

傳回之內容的內容所屬的排程器中的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

內容所屬的排程器中是唯一的內容識別碼。

##  <a name="getschedulegroupid"></a> GetScheduleGroupId

傳回內容目前正在使用排程群組的識別碼。

```
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>傳回值

目前正在處理內容上的 [排程] 群組的識別碼。

### <a name="remarks"></a>備註

這個方法的傳回值是排程群組的內容上所執行的瞬間取樣。 如果在非目前內容的其他內容上呼叫這個方法，則值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。

##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId

傳回虛擬處理器上目前執行內容識別碼。

```
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>傳回值

如果內容正在執行的虛擬處理器，內容目前正在執行，則虛擬處理器的識別碼否則，值`-1`。

### <a name="remarks"></a>備註

這個方法的傳回值是虛擬處理器上執行內容的瞬間取樣。 這個值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。

##  <a name="id"></a> Id

傳回目前內容中目前的內容所屬的排程器的唯一識別碼。

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>傳回值

如果目前的內容已連結至排程器 」，這是目前內容中排程器目前的內容屬於哪個; 唯一的識別項否則，值`-1`。

##  <a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling

指出是否會傳回工作集合目前正在執行內嵌於目前的內容正使用中的取消 （或會短時間內）。

```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>傳回值

如果排程器會附加至呼叫的內容及工作群組在該內容上執行的內嵌工作，指出是否該工作群組正使用中的取消作業 （或會短時間內）;否則，值`false`。

##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked

決定以同步方式封鎖的內容。 內容會被視為是如果它已明確地執行動作，導致封鎖，以同步方式會封鎖。

```
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>傳回值

是否會以同步方式封鎖的內容。

### <a name="remarks"></a>備註

內容會被視為是如果它已明確地執行動作，導致封鎖，以同步方式會封鎖。 在執行緒排程器上，這表示直接呼叫 `Context::Block` 方法或是使用 `Context::Block` 方法建置的同步處理物件。

這個方法的傳回值是以同步方式是否遭封鎖內容的瞬間完成範例。 此值可能會過期，因而會傳回僅適用於在非常特定的情況下。

##  <a name="operator_delete"></a> 運算子 delete

A`Context`終結物件內部執行階段。 不可將它明確刪除。

```
void operator delete(void* _PObject);
```

### <a name="parameters"></a>參數

*_PObject*<br/>
要刪除的物件指標。

##  <a name="oversubscribe"></a> 過度訂閱

插入的排程器的額外的虛擬處理器的其中一個虛擬處理器，在該排程器上執行的內容上叫用時的程式碼區塊的持續時間。

```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>參數

*_BeginOversubscription*<br/>
如果 **，則為 true**，過度訂閱期間，應新增的額外虛擬處理器的指示。 如果**false**，表示過度訂閱應該結束，而且應該移除先前加入的虛擬處理器。

##  <a name="schedulegroupid"></a> ScheduleGroupId

傳回目前的內容正在排程群組的識別碼。

```
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>傳回值

如果目前的內容會附加至排程器，並使用排程群組，排程器的識別碼群組目前的內容正在努力;否則，值`-1`。

##  <a name="unblock"></a> 解除封鎖

解除封鎖的內容，並使其成為可執行。

```
virtual void Unblock() = 0;
```

### <a name="remarks"></a>備註

它是完全合法呼叫`Unblock`方法來對應呼叫的前面[區塊](#block)方法。 只要呼叫`Block`和`Unblock`正確配對的方法，執行階段正確地處理自然的競爭情況的其中一個排序。 `Unblock`呼叫之前即將`Block`呼叫只是否定的效果`Block`呼叫。

有數個可以從這個方法會擲回的例外狀況。 如果內容嘗試呼叫`Unblock`方法本身[context_self_unblock](context-self-unblock-class.md)會擲回例外狀況。 如果呼叫`Block`和`Unblock`未正確配對 (例如，兩個呼叫`Unblock`會針對目前執行的內容)、 [context_unblock_unbalanced](context-unblock-unbalanced-class.md)會擲回例外狀況。

注意您的程式碼發行另一個執行緒可以呼叫其內容的位置的點之間是重要的期間`Unblock`方法和點的實際方法呼叫以`Block`為止。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 若要呼叫`Block`和`Unblock`方法不會追蹤封鎖和解除封鎖的原因。 只有一個物件應具備的擁有權`Block`和`Unblock`組。

##  <a name="virtualprocessorid"></a> VirtualProcessorId

傳回目前內容上所執行的虛擬處理器的識別碼。

```
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>傳回值

如果目前的內容已連結至排程器 」，這是目前的內容在; 執行的虛擬處理器的識別碼否則，值`-1`。

### <a name="remarks"></a>備註

這個方法的傳回值是目前的內容上所執行的虛擬處理器的瞬間取樣。 這個值傳回時可能會過期，因而無法依賴。 一般而言，這個方法會用於偵錯或追蹤之用。

##  <a name="yield"></a> yield

會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。

```
static void __cdecl Yield();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

##  <a name="yieldexecution"></a> YieldExecution

會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。

```
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

此函式的新 Visual Studio 2015 中，且等同[產生](#yield)函式，但與 Windows.h 中的 Yield 巨集不會衝突。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[Scheduler 類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

