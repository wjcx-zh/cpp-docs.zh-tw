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
ms.openlocfilehash: d888c7ba3d4a6680b2f77fef98d91c64825cda6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215825"
---
# <a name="context-class"></a>Context 類別

代表執行內容的抽象概念。

## <a name="syntax"></a>語法

```cpp
class Context;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|說明|
|----------|-----------------|
|[~ 內容的析構函式](#dtor)||

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[封鎖](#block)|封鎖目前的內容。|
|[CurrentCoNtext](#currentcontext)|傳回目前內容的指標。|
|[GetId](#getid)|傳回內容所屬排程器內唯一的內容識別碼。|
|[GetScheduleGroupId](#getschedulegroupid)|傳回內容目前正在處理之排程群組的識別碼。|
|[GetVirtualProcessorId](#getvirtualprocessorid)|傳回目前正在執行內容之虛擬處理器的識別碼。|
|[識別碼](#id)|針對目前內容所屬的排程器，傳回目前內容中唯一的識別碼。|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|傳回指示，指出目前內容上以內嵌方式執行的工作集合是否在作用中取消的過程中（或很快就會出現）。|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|判斷內容是否會同步封鎖。 如果內容明確執行導致封鎖的動作，則會將其視為同步封鎖。|
|[過度訂閱](#oversubscribe)|針對在該排程器中的其中一個虛擬處理器上執行的內容叫用時，會在程式碼區塊的持續時間內，將額外的虛擬處理器插入排程器中。|
|[ScheduleGroupId](#schedulegroupid)|傳回目前內容正在處理之排程群組的識別碼。|
|[作者](#unblock)|解除封鎖內容並使其變成可執行。|
|[VirtualProcessorId](#virtualprocessorid)|傳回目前內容執行所在的虛擬處理器的識別碼。|
|[看出](#yield)|會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。|

## <a name="remarks"></a>備註

並行執行階段排程器[（請參閱](scheduler-class.md)排程器）會使用執行內容來執行您的應用程式排入佇列的工作。 Win32 執行緒是在 Windows 作業系統上執行內容的範例。

排程器的並行層級會在任何時候，等於 Resource Manager 所授與的虛擬處理器數目。 虛擬處理器是處理資源的抽象概念，會對應到基礎系統上的硬體執行緒。 只有單一排程器內容可以在指定時間于虛擬處理器上執行。

排程器本質上是合作的，而且執行內容可以在想要進入等候狀態時，隨時將其虛擬處理器產生至不同的內容。 當它的等候滿足時，就無法繼續執行，直到排程器中的可用虛擬處理器開始執行為止。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Context`

## <a name="requirements"></a>需求

**標頭：** concrt。h

**命名空間：** 並行

## <a name="block"></a><a name="block"></a>總匯

封鎖目前的內容。

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

如果呼叫內容是在虛擬處理器上執行，則虛擬處理器會尋找另一個可執行檔內容，也可能會建立新的內容。

呼叫 `Block` 或將呼叫方法之後，您必須將它與另一個執行內容的[解除封鎖](#unblock)方法呼叫配對，才能讓它再次執行。 請注意，您的程式碼發佈其內容給另一個執行緒的時間點之間，要能夠呼叫 `Unblock` 方法以及實際方法呼叫的所在點之間，會有很長的期間 `Block` 。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 `Block`和方法的呼叫 `Unblock` 不會追蹤封鎖和解除封鎖的原因。 只有一個物件應有配對的擁有權 `Block` -  `Unblock` 。

這個方法可能會擲回各種例外狀況，包括[scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)。

## <a name="context"></a><a name="dtor"></a>~ 內容

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a><a name="currentcontext"></a>CurrentCoNtext

傳回目前內容的指標。

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>傳回值

目前內容的指標。

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

## <a name="getid"></a><a name="getid"></a>GetId

傳回內容所屬排程器內唯一的內容識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

內容所屬之排程器內唯一的內容識別碼。

## <a name="getschedulegroupid"></a><a name="getschedulegroupid"></a>GetScheduleGroupId

傳回內容目前正在處理之排程群組的識別碼。

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>傳回值

內容目前正在處理之排程群組的識別碼。

### <a name="remarks"></a>備註

這個方法的傳回值是執行內容之排程群組的即時取樣。 如果在非目前內容的其他內容上呼叫這個方法，則值傳回時可能會過期，因而無法依賴。 一般來說，這個方法只會用於偵錯工具或追蹤用途。

## <a name="getvirtualprocessorid"></a><a name="getvirtualprocessorid"></a>GetVirtualProcessorId

傳回目前正在執行內容之虛擬處理器的識別碼。

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>傳回值

如果內容目前正在虛擬處理器上執行，則為目前執行內容之虛擬處理器的識別碼;否則，值為 `-1` 。

### <a name="remarks"></a>備註

這個方法的傳回值，是內容執行所在的虛擬處理器的瞬間取樣。 這個值傳回時可能會過期，因而無法依賴。 一般來說，這個方法只會用於偵錯工具或追蹤用途。

## <a name="id"></a><a name="id"></a>號

針對目前內容所屬的排程器，傳回目前內容中唯一的識別碼。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>傳回值

如果目前內容附加至排程器，則為目前內容所屬之排程器內唯一的目前內容識別碼;否則，值為 `-1` 。

## <a name="iscurrenttaskcollectioncanceling"></a><a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling

傳回指示，指出目前內容上以內嵌方式執行的工作集合是否在作用中取消的過程中（或很快就會出現）。

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>傳回值

如果排程器附加至呼叫內容，而工作組正在執行該內容的內嵌工作，則表示該工作組是否在作用中取消的過程中（或很快就會出現）;否則，值為 **`false`** 。

## <a name="issynchronouslyblocked"></a><a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked

判斷內容是否會同步封鎖。 如果內容明確執行導致封鎖的動作，則會將其視為同步封鎖。

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>傳回值

是否同步封鎖內容。

### <a name="remarks"></a>備註

如果內容明確執行導致封鎖的動作，則會將其視為同步封鎖。 在執行緒排程器上，這表示直接呼叫 `Context::Block` 方法或是使用 `Context::Block` 方法建置的同步處理物件。

這個方法的傳回值，是內容是否同步封鎖的瞬間範例。 這個值在傳回時可能會過時，而且只能在非常特定的情況下使用。

## <a name="operator-delete"></a><a name="operator_delete"></a>運算子 delete

`Context`物件會在執行時間于內部終結。 不可將它明確刪除。

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>參數

*_PObject*<br/>
要刪除之物件的指標。

## <a name="oversubscribe"></a><a name="oversubscribe"></a>過度訂閱

針對在該排程器中的其中一個虛擬處理器上執行的內容叫用時，會在程式碼區塊的持續時間內，將額外的虛擬處理器插入排程器中。

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>參數

*_BeginOversubscription*<br/>
如果 **`true`** 為，表示應該在超額訂閱期間新增額外的虛擬處理器。 如果為 **`false`** ，表示超額訂閱應該結束，而且應該移除先前新增的虛擬處理器。

## <a name="schedulegroupid"></a><a name="schedulegroupid"></a>ScheduleGroupId

傳回目前內容正在處理之排程群組的識別碼。

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>傳回值

如果目前的內容附加至排程器，並在排程群組上運作，則為目前內容所使用之排程器群組的識別碼;否則，值為 `-1` 。

## <a name="unblock"></a><a name="unblock"></a>作者

解除封鎖內容並使其變成可執行。

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>備註

對方法的呼叫 `Unblock` 在對[Block](#block)方法進行對應呼叫之前，是完全合法的。 只要對和方法的呼叫 `Block` `Unblock` 都已正確配對，執行時間就會適當地處理任一順序的自然競爭。 呼叫 `Unblock` 前的呼叫 `Block` 只會否定呼叫的效果 `Block` 。

有幾個例外狀況可以從這個方法擲回。 如果內容嘗試 `Unblock` 在本身上呼叫方法，將會擲回[coNtext_self_unblock](context-self-unblock-class.md)例外狀況。 如果對的 `Block` 呼叫 `Unblock` 未正確配對（例如，對目前正在執行的 `Unblock` 內容進行兩個呼叫），則會擲回[coNtext_unblock_unbalanced](context-unblock-unbalanced-class.md)例外狀況。

請注意，您的程式碼發佈其內容給另一個執行緒的時間點之間，要能夠呼叫 `Unblock` 方法以及實際方法呼叫的所在點之間，會有很長的期間 `Block` 。 在這個過程中，您不能呼叫因本身原因而封鎖及解除封鎖的任何方法 (例如，取得鎖定)。 `Block`和方法的呼叫 `Unblock` 不會追蹤封鎖和解除封鎖的原因。 只有一個物件應具有和配對的擁有權 `Block` `Unblock` 。

## <a name="virtualprocessorid"></a><a name="virtualprocessorid"></a>VirtualProcessorId

傳回目前內容執行所在的虛擬處理器的識別碼。

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>傳回值

如果目前內容附加至排程器，則為目前內容執行所在之虛擬處理器的識別碼;否則，值為 `-1` 。

### <a name="remarks"></a>備註

這個方法的傳回值是目前內容執行所在的虛擬處理器的即時取樣。 這個值傳回時可能會過期，因而無法依賴。 一般來說，這個方法只會用於偵錯工具或追蹤用途。

## <a name="yield"></a><a name="yield"></a>看出

會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

## <a name="yieldexecution"></a><a name="yieldexecution"></a>YieldExecution

會產生執行，以便能夠執行其他內容。 如果沒有其他內容需要產生，排程器即會配合其他作業系統執行緒。

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>備註

如果呼叫的內容目前沒有任何相關聯的排程器，則這個方法會將處理序的預設排程器建立及/或附加至呼叫的內容。

此函式是 Visual Studio 2015 中的新功能，與[yield](#yield)函式相同，但不會與 Windows. h 中的 yield 宏衝突。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[排程器類別](scheduler-class.md)<br/>
[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
