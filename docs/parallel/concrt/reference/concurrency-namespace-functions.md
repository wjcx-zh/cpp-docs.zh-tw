---
title: concurrency 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 25cd74e20102bbc1a75e4b4efe1bf234845f7fcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840176"
---
# <a name="concurrency-namespace-functions"></a>concurrency 命名空間函式

:::row:::
   :::column span="":::
      [`Alloc`](#alloc)\
      [`asend`](#asend)\
      [`cancel_current_task`](#cancel_current_task)\
      [`clear`](#clear)\
      [`create_async`](#create_async)\
      [`create_task`](#create_task)\
      [`CreateResourceManager`](#createresourcemanager)\
      [`DisableTracing`](#disabletracing)\
      [`EnableTracing`](#enabletracing)\
      [`Free`](#free)\
      [`get_ambient_scheduler`](#get_ambient_scheduler)\
      [`GetExecutionContextId`](#getexecutioncontextid)\
      [`GetOSVersion`](#getosversion)\
      [`GetProcessorCount`](#getprocessorcount)\
      [`GetProcessorNodeCount`](#getprocessornodecount)
   :::column-end:::
   :::column span="":::
      [`GetSchedulerId`](#getschedulerid)\
      [`internal_assign_iterators`](#internal_assign_iterators)\
      [`interruption_point`](#interruption_point)\
      [`is_current_task_group_canceling`](#is_current_task_group_canceling)\
      [`make_choice`](#make_choice)\
      [`make_greedy_join`](#make_greedy_join)\
      [`make_join`](#make_join)\
      [`make_task`](#make_task)\
      [`parallel_buffered_sort`](#parallel_buffered_sort)\
      [`parallel_for_each`](#parallel_for_each)\
      [`parallel_for`](#parallel_for)\
      [`parallel_invoke`](#parallel_invoke)\
      [`parallel_radixsort`](#parallel_radixsort)\
      [`parallel_reduce`](#parallel_reduce)\
      [`parallel_sort`](#parallel_sort)
   :::column-end:::
   :::column span="":::
      [`parallel_transform`](#parallel_transform)\
      [`receive`](#receive)\
      [`run_with_cancellation_token`](#run_with_cancellation_token)\
      [`send`](#send)\
      [`set_ambient_scheduler`](#set_ambient_scheduler)\
      [`set_task_execution_resources`](#set_task_execution_resources)\
      [`swap`](#swap)\
      [`task_from_exception`](#task_from_exception)\
      [`task_from_result`](#task_from_result)\
      [`Trace_agents_register_name`](#trace_agents_register_name)\
      [`try_receive`](#try_receive)\
      [`wait`](#wait)\
      [`when_all`](#when_all)\
      [`when_any`](#when_any)
   :::column-end:::
:::row-end:::

## <a name="alloc"></a><a name="alloc"></a> 配置

會透過並行執行階段的快取子配置器指定的大小，來配置記憶體區塊。

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>參數

*_NumBytes*<br/>
要配置的記憶體位元組數目。

### <a name="return-value"></a>傳回值

新配置之記憶體的指標。

### <a name="remarks"></a>備註

如需應用程式中哪些案例可以從使用快取子配置器獲益的詳細資訊，請參閱 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

## <a name="asend"></a><a name="asend"></a> asend

非同步傳送作業，會排程工作將資料傳播到目標區塊。

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>參數

*T*<br/>
要傳送之資料的型別。

*_Trg*<br/>
傳送資料之目標的指標或參考。

*_Data*<br/>
要傳送之資料的參考。

### <a name="return-value"></a>傳回值

**`true`** 如果在傳回方法之前接受訊息，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [訊息傳遞函數](../../../parallel/concrt/message-passing-functions.md)。

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a> cancel_current_task

取消目前執行的工作。 這個函式可以從工作主體內呼叫，以中止工作執行並導致它進入 `canceled` 狀態。

如果不是在 `task` 的主體中，這就不是支援呼叫這個函式的情況。 這麼做會導致未定義的行為，例如當應用程式中的損毀或無回應。

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a> 清楚

清除並行佇列，終結任何目前已排入佇列的元素。 這個方法不是平行存取安全的。

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>參數

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a> create_async

以使用者提供的 Lambda 或函式物件為基礎，建立 Windows 執行階段非同步建構。 根據傳遞至方法的 Lambda 簽章，`create_async` 的傳回型別是下列其中一個：`IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^`。

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>參數

*_Function*<br/>
輸入 。

*_Func*<br/>
從中建立 Windows 執行階段非同步建構的 Lambda 或函式物件。

### <a name="return-value"></a>傳回值

以 IAsyncAction ^、Iasyncactionwithprogress<tprogress> iasyncoperation<tresult> \<TProgress> ^、iasyncoperation<tresult>HTTP \<TResult> ^ 或 IAsyncOperationWithProgress ^ 表示的非同步結構 \<TResult, TProgress> 。 傳回的介面依賴傳遞至函式的 Lambda 簽章。

### <a name="remarks"></a>備註

Lambda 的傳回類型決定建構是動作或作業。

傳回 void 的 Lambda 造成動作的建立。 傳回屬於 `TResult` 類型之結果的 Lambda 會造成 TResult 作業的建立。

Lambda 可能也會傳回 `task<TResult>`，將非同步工作封裝在本身內或是表示非同步工作的工作鏈結的接續作業。 在這種情況下，Lambda 本身是內嵌執行，因為工作是非同步執行的工作，而且 Lambda 的傳回類型會解除包裝以產生 `create_async` 所傳回的非同步建構。 這表示傳回工作的 lambda \<void> 會造成動作的建立，而傳回工作的 lambda \<TResult> 將會造成 TResult 作業的建立。

Lambda 可以接受零個、一個或兩個引數。 有效的引數為 `progress_reporter<TProgress>` 和 `cancellation_token`，兩者都使用時依此順序。 沒有引數的 Lambda 會導致建立沒有進度報告功能的非同步建構。 接受 progress_reporter 的 lambda \<TProgress> 會導致 `create_async` 傳回非同步結構，而此結構會在每次呼叫 progress_reporter 物件的方法時，回報 TProgress 型別的進度 `report` 。 接受 cancellation_token 的 Lambda 可能使用該語彙基元來檢查取消的狀態，或是將語彙基元傳遞給所建立的工作，讓非同步建構的取消導致取消這些工作。

如果 lambda 或函式物件的主體傳回 (而非工作) 的結果 \<TResult> ，則會以非同步方式在進程 MTA 內于執行時間隱含為其建立的工作內容中執行 lambda。 `IAsyncInfo::Cancel` 方法會導致取消隱含工作。

如果 Lambda 的主體傳回工作，則 Lambda 會內嵌執行，而且藉由宣告 Lambda 接受屬於類型 `cancellation_token` 的引數，您可以觸發任何工作的取消作業，這些工作是您建立工作時，透過傳入該語彙基元，在 Lambda 建立的。 您也可以在語彙基元使用 `register_callback` 方法，使執行階段在您在非同步作業或產生的動作呼叫 `IAsyncInfo::Cancel` 時叫用回呼。

此函數僅適用于 Windows 執行階段應用程式。

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a> CreateResourceManager

傳回代表並行執行階段資源管理員單一執行個體的介面。 資源管理員會負責將資源指派給想要與彼此相互合作的排程器。

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>傳回值

`IResourceManager` 介面。

### <a name="remarks"></a>備註

對這個方法的多次後續呼叫將會傳回相同的 Resource Manager 實例。 每次呼叫方法都會遞增 Resource Manager 上的參考計數，而且當排程器完成與 Resource Manager 的通訊時，必須與 [IResourceManager：： Release](iresourcemanager-structure.md) 方法的呼叫相符。

如果並行執行階段不支援作業系統，則會擲回[unsupported_os](unsupported-os-class.md) 。

## <a name="create_task"></a><a name="create_task"></a> create_task

建立 PPL [task](task-class.md) 物件。 您可以在任何會使用工作建構函式的地方使用 `create_task`。 這主要是為了方便起見所提供，因為它允許在 **`auto`** 建立工作時使用關鍵字。

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>參數

*T*<br/>
從中要建構工作的參數的類型。

*_ReturnType*<br/>
輸入 。

*_Param*<br/>
從中要建構工作的參數。 如果您在 UWP 應用程式中使用工作，這可以是 lambda 或函式物件、 `task_completion_event` 物件、不同的 `task` 物件或 Windows：： Foundation：： IAsyncInfo 介面。

*_TaskOptions*<br/>
工作選項。

*_Task*<br/>
要建立的工作。

### <a name="return-value"></a>傳回值

型別為的新工作 `T` ，是從推斷而來 `_Param` 。

### <a name="remarks"></a>備註

第一個多載的行為就像是採用單一參數的工作函式。

第二個多載會將所提供的取消權杖與新建立的工作產生關聯。 如果您使用此多載，則不允許傳入不同的 `task` 物件做為第一個參數。

傳回的工作類型是從函式的第一個參數推斷而來。 如果 `_Param` 是 `task_completion_event<T>` 、或傳回 `task<T>` 類型或的仿函數，則建立的 `T` 工作 `task<T>` 類型為 `task<T>` 。

在 UWP 應用程式中，如果 `_Param` 是 Windows：： foundation：： iasyncoperation<tresult>HTTP \<T> ^ 或 windows：： foundation：： IAsyncOperationWithProgress ^ 的類型，或是傳回其中 \<T,P> 一種類型的仿函數，則建立的工作將為類型 `task<T>` 。 如果 `_Param` 是 Windows：： foundation：： IAsyncAction ^ 或 windows：： foundation：： iasyncactionwithprogress<tprogress> iasyncoperation<tresult> ^ 的型別， \<P> 或傳回其中一種類型的仿函數，則建立的工作會有類型 `task<void>` 。

## <a name="disabletracing"></a><a name="disabletracing"></a> DisableTracing

停用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已移除註冊而被取代。

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>傳回值

如果已正確停用追蹤， `S_OK` 則會傳回。 如果先前未啟始追蹤，則會傳回 `E_NOT_STARTED`

## <a name="enabletracing"></a><a name="enabletracing"></a> EnableTracing

啟用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已開啟而被取代。

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>傳回值

如果已正確起始追蹤，則 `S_OK` 會傳回，否則 `E_NOT_STARTED` 會傳回。

## <a name="free"></a><a name="free"></a> 自由

釋放先前由 `Alloc` 方法配置的記憶體區塊至並行執行階段的快取子配置器。

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>參數

*_PAllocation*<br/>
要釋放的方法先前配置的記憶體指標 `Alloc` 。 如果參數 `_PAllocation` 設定為值 `NULL` ，此方法將會忽略它並立即傳回。

### <a name="remarks"></a>備註

如需應用程式中哪些案例可以從使用快取子配置器獲益的詳細資訊，請參閱 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a> get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>傳回值

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a> GetExecutionCoNtextId

傳回可指派給實作 `IExecutionContext` 介面之執行內容的唯一識別碼。

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>傳回值

執行內容的唯一識別碼。

### <a name="remarks"></a>備註

您可以使用這個方法來取得執行內容的識別碼，然後再將 `IExecutionContext` 介面做為參數傳遞給 Resource Manager 所提供的任何方法。

## <a name="getosversion"></a><a name="getosversion"></a> GetOSVersion

傳回作業系統版本。

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>傳回值

代表作業系統的列舉值。

### <a name="remarks"></a>備註

如果並行執行階段不支援作業系統，則會擲回[unsupported_os](unsupported-os-class.md) 。

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a> GetProcessorCount

傳回基礎系統上的硬體執行緒數目。

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>傳回值

硬體執行緒的數目。

### <a name="remarks"></a>備註

如果並行執行階段不支援作業系統，則會擲回[unsupported_os](unsupported-os-class.md) 。

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a> GetProcessorNodeCount

傳回基礎系統上的 NUMA 節點或處理器套件數目。

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>傳回值

NUMA 節點或處理器封裝的數目。

### <a name="remarks"></a>備註

如果系統包含比處理器套件更多的 NUMA 節點，則會傳回 NUMA 節點的數目，否則會傳回處理器套件的數目。

如果並行執行階段不支援作業系統，則會擲回[unsupported_os](unsupported-os-class.md) 。

## <a name="getschedulerid"></a><a name="getschedulerid"></a> GetSchedulerId

傳回可指派給實作 `IScheduler` 介面之排程器的唯一識別碼。

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>傳回值

排程器的唯一識別碼。

### <a name="remarks"></a>備註

您可以使用這個方法來取得排程器的識別碼，然後再將 `IScheduler` 介面做為參數傳遞給 Resource Manager 所提供的任何方法。

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a> internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>參數

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a> interruption_point

建立取消的中斷點。 如果這個函式呼叫的內容正在取消，則會擲出中止目前執行之平行工作執行的內部例外狀況。 如果取消不在進行中，函式不會執行任何動作。

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>備註

您不應該攔截 `interruption_point()` 函式擲回的內部取消例外狀況。 例外狀況會由執行階段攔截並處理，而攔截它可能會造成程式行為異常。

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a> is_current_task_group_canceling

傳回指示，以說明目前正以內嵌方式在目前內容上執行的工作群組是否正在取消 (或即將取消)。 請注意，如果目前的內容目前沒有以內嵌方式執行的工作組， **`false`** 則會傳回。

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>傳回值

**`true`** 如果正在取消目前正在執行的工作組，則為， **`false`** 否則為。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。

## <a name="make_choice"></a><a name="make_choice"></a> make_choice

從選擇性的 `choice` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>參數

*T1*<br/>
第一個來源的訊息區塊類型。

*T2*<br/>
第二個來源的訊息區塊類型。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。

*_Item1*<br/>
第一個來源。

*_Item2*<br/>
第二個來源。

*_Items*<br/>
其他來源。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="return-value"></a>傳回值

有兩個或多個輸入來源的 `choice` 訊息區塊。

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a> make_greedy_join

從選擇性的 `greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>參數

*T1*<br/>
第一個來源的訊息區塊類型。

*T2*<br/>
第二個來源的訊息區塊類型。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。

*_Item1*<br/>
第一個來源。

*_Item2*<br/>
第二個來源。

*_Items*<br/>
其他來源。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="return-value"></a>傳回值

有兩個或多個輸入來源的 `greedy multitype_join` 訊息區塊。

## <a name="make_join"></a><a name="make_join"></a> make_join

從選擇性的 `non_greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>參數

*T1*<br/>
第一個來源的訊息區塊類型。

*T2*<br/>
第二個來源的訊息區塊類型。

*_PScheduler*<br/>
`Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。

*_Item1*<br/>
第一個來源。

*_Item2*<br/>
第二個來源。

*_Items*<br/>
其他來源。

*_PScheduleGroup*<br/>
`ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。

### <a name="return-value"></a>傳回值

有兩個或多個輸入來源的 `non_greedy multitype_join` 訊息區塊。

## <a name="make_task"></a><a name="make_task"></a> make_task

建立 `task_handle` 物件的 Factory 方法。

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>參數

*_Function*<br/>
將叫用來執行物件所代表之工作的函式物件類型 `task_handle` 。

*_Func*<br/>
將叫用以執行物件所代表之工作的函式 `task_handle` 。 這可能是 lambda 仿函數、函式的指標，或任何支援具有簽章的函式呼叫運算子版本的物件 `void operator()()` 。

### <a name="return-value"></a>傳回值

`task_handle` 物件。

### <a name="remarks"></a>備註

當您需要使用 lambda 運算式來建立物件時，此函式會很有用 `task_handle` ，因為它可讓您建立物件，而不需要知道 lambda 仿函數的真正類型。

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a> parallel_buffered_sort

以平行方式將指定範圍中的專案排列成非遞減順序，或根據二元述詞指定的順序準則。 這個函式語意與 `std::sort` 類似：皆是以比較為基礎、不穩定、就地排序的；差別為它需要 `O(n)` 額外的空間，且必須預設初始化需排序的項目。

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>參數

*_Random_iterator*<br/>
輸入範圍的迭代器類型。

*_Allocator*<br/>
C + + 標準程式庫相容記憶體配置器的類型。

*_Function*<br/>
二元比較子的類型。

*_Begin*<br/>
隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。

*_End*<br/>
隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。

*_Alloc*<br/>
C + + 標準程式庫相容記憶體配置器的實例。

*_Func*<br/>
使用者定義的述詞函式物件，用來定義順序中後續項目應符合的比較準則。 二元述詞會採用兩個引數，並 **`true`** 在滿足和 **`false`** 不滿意時傳回。 這個比較子函式必須對序列中項目的配對強制執行嚴格的弱式順序。

*_Chunk_size*<br/>
要分割成兩個進行並行執行的最小區塊大小。

### <a name="remarks"></a>備註

所有多載都需要 `n * sizeof(T)` 額外的空間，其中 `n` 是要排序的專案數目，而 `T` 是元素類型。 在大部分的情況下 parallel_buffered_sort 會在 [parallel_sort](concurrency-namespace-functions.md)中顯示效能改善，如果您有可用的記憶體，則應該將它用於 parallel_sort。

如果您未提供二元比較子做為 `std::less` 預設值，則需要專案類型才能提供運算子 `operator<()` 。

如果您未提供配置器類型或實例，則會使用 c + + 標準程式庫記憶體 `std::allocator<T>` 配置器來配置緩衝區。

演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性引數 `_Chunk_size` 可以用來向演算法指出它應該處理大小 < 順序的區塊 `_Chunk_size` 。

## <a name="parallel_for"></a><a name="parallel_for"></a> parallel_for

`parallel_for` 會逐一查看某個範圍的索引，並以平行方式在每個反覆項目上執行使用者提供的函式。

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>參數

*_Index_type*<br/>
用於反復專案的索引類型。

*_Function*<br/>
將在每個反復專案執行的函數類型。

*_Partitioner*<br/>
用來分割所提供範圍的分割區類型。

*first*<br/>
要包含在反覆運算中的第一個索引。

*last*<br/>
要包含在反覆運算中的最後一個索引之後的索引。

*_Step*<br/>
逐一查看至時，所依據的步驟 `first` 值 `last` 。 此步驟必須是正數。 如果步驟小於1，則會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md) 。

*_Func*<br/>
要在每個反復專案執行的函數。 這可能是 lambda 運算式、函式指標或任何支援具有簽章的函式呼叫運算子版本的物件 `void operator()(_Index_type)` 。

*_Part*<br/>
Partitioner 物件的參考。 引數可以是 **`const`** [auto_partitioner](auto-partitioner-class.md) `&` 、 **`const`** [static_partitioner](static-partitioner-class.md) `&` 、 **`const`** [simple_partitioner](simple-partitioner-class.md) `&` 或[affinity_partitioner](affinity-partitioner-class.md) `&` 如果使用[affinity_partitioner](affinity-partitioner-class.md)物件，則參考必須是非 const 的左值參考，如此一來，演算法就可以儲存狀態，以便日後重複使用迴圈。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [平行演算法](../../../parallel/concrt/parallel-algorithms.md)。

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a> parallel_for_each

`parallel_for_each` 會平行套用指定的函式到範圍內的每個項目。 在語意上，它相當於 `std` 命名空間中的 `for_each` 函式，但項目的反覆項目會平行執行，而且不會指定反覆項目的順序。 `_Func` 引數必須支援 `operator()(T)` 形式的函式呼叫運算子，其中 `T` 參數是要逐一查看之容器的項目類型。

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
用來反復查看容器的反覆運算器類型。

*_Function*<br/>
將套用至範圍內每個元素的函式類型。

*_Partitioner*<br/>
*first*<br/>
反覆運算器，定址要包含在平行反覆運算中的第一個元素的位置。

*last*<br/>
反覆運算器，定址要包含在平行反覆運算中的最後一個元素之後的位置。

*_Func*<br/>
套用至範圍中每個元素的使用者定義函數物件。

*_Part*<br/>
Partitioner 物件的參考。 引數可以是 **`const`** [auto_partitioner](auto-partitioner-class.md) `&` 、 **`const`** [static_partitioner](static-partitioner-class.md) `&` 、 **`const`** [simple_partitioner](simple-partitioner-class.md) `&` 或[affinity_partitioner](affinity-partitioner-class.md) `&` 如果使用[affinity_partitioner](affinity-partitioner-class.md)物件，則參考必須是非 const 的左值參考，如此一來，演算法就可以儲存狀態，以便日後重複使用迴圈。

### <a name="remarks"></a>備註

如果沒有明確的對應程式，則會將[auto_partitioner](auto-partitioner-class.md)用於多載。

對於不支援隨機存取的反覆運算器，只支援 [auto_partitioner](auto-partitioner-class.md) 。

如需詳細資訊，請參閱 [平行演算法](../../../parallel/concrt/parallel-algorithms.md)。

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a> parallel_invoke

平行執行提供作為參數的函式物件，並加以封鎖直到完成執行為止。 函式物件可能是 Lambda 運算式、函式指標，或是支援函式呼叫運算子與簽章 `void operator()()` 版本的任何物件。

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>參數

*_Function1*<br/>
要平行執行的第一個函式物件的型別。

*_Function2*<br/>
要平行執行的第二個函式物件的型別。

*_Function3*<br/>
要平行執行的第三個函式物件的型別。

*_Function4*<br/>
要平行執行的第四個函式物件的型別。

*_Function5*<br/>
要平行執行的第五個函式物件的型別。

*_Function6*<br/>
要平行執行的第六個函式物件的型別。

*_Function7*<br/>
要平行執行的第七個函式物件的型別。

*_Function8*<br/>
要平行執行的第八個函式物件的型別。

*_Function9*<br/>
要平行執行的第九個函式物件的型別。

*_Function10*<br/>
要平行執行的第十個函式物件的型別。

*_Func1*<br/>
要平行執行的第一個函式物件。

*_Func2*<br/>
要平行執行的第二個函式物件。

*_Func3*<br/>
要平行執行的第三個函式物件。

*_Func4*<br/>
要平行執行的第四個函式物件。

*_Func5*<br/>
要平行執行的第五個函式物件。

*_Func6*<br/>
要平行執行的第六個函式物件。

*_Func7*<br/>
要平行執行的第七個函式物件。

*_Func8*<br/>
要平行執行的第八個函式物件。

*_Func9*<br/>
要平行執行的第九個函式物件。

*_Func10*<br/>
要平行執行的第十個函式物件。

### <a name="remarks"></a>備註

請注意，提供做為參數的一或多個函式物件，可能會在呼叫內容上以內嵌方式執行。

如果一或多個做為參數傳遞給此函式的函式物件擲回例外狀況，則執行時間會選取其中一個例外狀況，並將其從呼叫中傳播出去 `parallel_invoke` 。

如需詳細資訊，請參閱 [平行演算法](../../../parallel/concrt/parallel-algorithms.md)。

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a> parallel_radixsort

使用基數排序演算法，將指定範圍內的項目排列成非遞減順序。 這是一個穩定的排序函式，其需要可將項目排序成不帶正負號的整數機碼的投影函式。 要排序的項目都必須進行預設初始化。

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>參數

*_Random_iterator*<br/>
輸入範圍的迭代器類型。

*_Allocator*<br/>
C + + 標準程式庫相容記憶體配置器的類型。

*_Function*<br/>
投射函數的型別。

*_Begin*<br/>
隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。

*_End*<br/>
隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。

*_Alloc*<br/>
C + + 標準程式庫相容記憶體配置器的實例。

*_Proj_func*<br/>
將元素轉換成整數值的使用者定義投射函數物件。

*_Chunk_size*<br/>
要分割成兩個進行並行執行的最小區塊大小。

### <a name="remarks"></a>備註

所有多載都需要 `n * sizeof(T)` 額外的空間，其中 `n` 是要排序的專案數目，而 `T` 是元素類型。 具有簽章的一元投影仿函數 `I _Proj_func(T)` 需要在指定專案時傳回索引鍵，其中 `T` 是元素類型，而 `I` 是不帶正負號的整數類型。

如果您未提供投射函數，則只會傳回元素的預設投射函數會用於整數類資料類型。 如果專案不是有投射函數的整數類資料類型，則函數將無法編譯。

如果您未提供配置器類型或實例，則會使用 c + + 標準程式庫記憶體 `std::allocator<T>` 配置器來配置緩衝區。

演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性引數 `_Chunk_size` 可以用來向演算法指出它應該處理大小 < 順序的區塊 `_Chunk_size` 。

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a> parallel_reduce

以平行方式，透過計算後繼元素的部分總和來計算在一定範圍內所有項目的總和，或是計算部分後繼結果 (取得方式是使用指定的二進位運算而非總和運算得出) 的結果。 `parallel_reduce` 語意與 `std::accumulate` 類似；不同的是，它需要關聯的二進位運算，而且需要識別值而不是初始值。

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>參數

*_Forward_iterator*<br/>
輸入範圍的反覆運算器類型。

*_Sym_reduce_fun*<br/>
對稱縮減函數的類型。 這必須是具有簽章的函式類型 `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)` ，其中 _Reduce_type 與身分識別類型和縮減的結果類型相同。 在第三個多載中，這應該與的輸出類型一致 `_Range_reduce_fun` 。

*_Reduce_type*<br/>
輸入將縮減為的類型，這可能與輸入元素類型不同。 傳回值和識別值將會有這種類型。

*_Range_reduce_fun*<br/>
範圍縮減函數的類型。 這必須是具有簽章的函式類型 `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)` ，_Reduce_type 與識別類型和縮減的結果類型相同。

*_Begin*<br/>
輸入反覆運算器，定址要減少之範圍中的第一個元素。

*_End*<br/>
輸入反覆運算器，用於定址要減少之範圍中最後一個元素以外的元素。

*_Identity*<br/>
識別值的 `_Identity` 類型與減少的結果型別相同，也是 `value_type` 第一個和第二個多載的反覆運算器。 針對第三個多載，識別值的類型必須與減少的結果型別相同，但可能與反覆運算器的不同 `value_type` 。 它必須具有適當的值，讓範圍減少運算子套用 `_Range_fun` 至類型的單一元素範圍 `value_type` 和識別值時，其行為就像是從類型轉換 `value_type` 成識別類型的類型。

*_Sym_fun*<br/>
將在縮減的第二個中使用的對稱函數。 如需詳細資訊，請參閱備註。

*_Range_fun*<br/>
將在縮減的第一個階段中使用的函數。 如需詳細資訊，請參閱備註。

### <a name="return-value"></a>傳回值

減少的結果。

### <a name="remarks"></a>備註

為了執行平行減少，函式會根據基礎排程器可用的背景工作數目，將範圍分割成區塊。 減少會在兩個階段中進行，第一個階段會在每個區塊內執行縮減，而第二個階段則會在每個區塊的部分結果之間減少。

第一個多載需要 iterator 的 `value_type` 、 `T` ，與識別值型別和縮減結果型別相同。 元素類型 T 必須提供運算子 `T T::operator + (T)` ，以減少每個區塊中的元素。 第二個階段也會使用相同的運算子。

第二個多載也需要 iterator 與 `value_type` 識別值型別和縮減結果型別相同。 提供的二元運算子 `_Sym_fun` 會在兩個階段中使用，並以識別值作為第一個階段的初始值。

針對第三個多載，識別值型別必須與縮減結果型別相同，但反覆運算器 `value_type` 可能與兩者不同。 範圍縮減函數 `_Range_fun` 會在第一個階段使用，並以識別值作為初始值，而二元函數 `_Sym_reduce_fun` 會套用至第二個階段中的子結果。

## <a name="parallel_sort"></a><a name="parallel_sort"></a> parallel_sort

以平行方式將指定範圍中的專案排列成非遞減順序，或根據二元述詞指定的順序準則。 這個函式語意與 `std::sort` 類似，皆是以比較為基礎、不穩定、就地排序的。

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>參數

*_Random_iterator*<br/>
輸入範圍的迭代器類型。

*_Function*<br/>
二元比較子仿函數 (functor) 的類型。

*_Begin*<br/>
隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。

*_End*<br/>
隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。

*_Func*<br/>
使用者定義的述詞函式物件，用來定義順序中後續項目應符合的比較準則。 二元述詞會採用兩個引數，並 **`true`** 在滿足和 **`false`** 不滿意時傳回。 這個比較子函式必須對序列中項目的配對強制執行嚴格的弱式順序。

*_Chunk_size*<br/>
區塊的大小下限，會分割成兩個以進行平行執行。

### <a name="remarks"></a>備註

第一個多載會使用二元比較子 `std::less` 。

第二個多載會使用提供的二元比較子，該比較子應具有 `bool _Func(T, T)` 簽章，其中 `T` 是輸入範圍中項目的類型。

演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性引數 `_Chunk_size` 可以用來向演算法指出它應該處理大小 < 順序的區塊 `_Chunk_size` 。

## <a name="parallel_transform"></a><a name="parallel_transform"></a> parallel_transform

以平行方式，將指定的函式物件套用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。 此函式在語意上等於 `std::transform`。

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>參數

*_Input_iterator1*<br/>
第一個或唯一一個輸入迭代器的類型。

*_Output_iterator*<br/>
輸出反覆運算器的類型。

*_Unary_operator*<br/>
在輸入範圍內的每個項目上執行的一元仿函數 (functor) 類型。

*_Input_iterator2*<br/>
第二個輸入迭代器的類型。

*_Binary_operator*<br/>
在兩個來源範圍的項目上成對執行的二元仿函數 (functor) 類型。

*_Partitioner*<br/>
*first1*<br/>
輸入迭代器，用於定址在第一個或唯一一個來源範圍上執行之第一個項目的位置。

*last1*<br/>
輸入迭代器，用於定址超過要在第一個或唯一一個來源範圍中執行之最後一個項目的第一個位置。

*_Result*<br/>
輸出迭代器，用於定址目的範圍中第一個項目的位置。

*_Unary_op*<br/>
套用至來源範圍中每個項目的使用者定義一元函式物件。

*_Part*<br/>
Partitioner 物件的參考。 引數可以是 **`const`** [auto_partitioner](auto-partitioner-class.md) `&` 、 **`const`** [static_partitioner](static-partitioner-class.md) `&` 、 **`const`** [simple_partitioner](simple-partitioner-class.md) `&` 或[affinity_partitioner](affinity-partitioner-class.md) `&` 如果使用[affinity_partitioner](affinity-partitioner-class.md)物件，則參考必須是非 const 的左值參考，如此一來，演算法就可以儲存狀態，以便日後重複使用迴圈。

*first2*<br/>
輸入迭代器，用於定址第二個來源範圍中要執行之第一個項目的位置。

*_Binary_op*<br/>
使用者定義的二元函式物件，它會以正向順序成對套用至兩個來源範圍。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址超過接收函式物件所轉換之輸出項目的目的範圍中最後一個項目的第一個位置。

### <a name="remarks"></a>備註

[auto_partitioner](auto-partitioner-class.md) 將用於沒有明確分割的引數的多載。

對於不支援隨機存取的反覆運算器，只支援 [auto_partitioner](auto-partitioner-class.md) 。

採用 `_Unary_op` 引數的多載會透過將一元仿函數套用至輸出範圍中的每個項目，將輸入範圍轉換成輸出範圍。 `_Unary_op` 必須支援具有 `operator()(T)` 簽章的函式呼叫運算子，其中 `T` 是反覆查看之範圍的實值類型。

採用 `_Binary_op` 引數的多載會透過將二元仿函數套用至第一個輸入範圍的某一個項目和第二個輸入範圍的某一個項目，將兩個輸入範圍轉換成輸出範圍。 `_Binary_op` 必須支援具有 `operator()(T, U)` 簽章的函式呼叫運算子，其中 `T`、`U` 為兩個輸入迭代器的實值類型。

如需詳細資訊，請參閱 [平行演算法](../../../parallel/concrt/parallel-algorithms.md)。

## <a name="receive"></a><a name="receive"></a> 收到

一般接收實作，可讓內容等候來自一個來源的資料，並且篩選所接受的值。

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>參數

*T*<br/>
裝載類型。

*_Src*<br/>
預期資料的來源指標或參考。

*_Timeout*<br/>
資料的最長時間（以毫秒為單位）。

*_Filter_proc*<br/>
判斷是否應接受訊息的篩選函數。

### <a name="return-value"></a>傳回值

來源中裝載類型的值。

### <a name="remarks"></a>備註

如果參數的 `_Timeout` 值不是常數 `COOPERATIVE_TIMEOUT_INFINITE` ，則會在收到訊息之前指定的時間量過期時擲回例外狀況 [operation_timed_out](operation-timed-out-class.md) 。 如果您想要長度為零的長度，則應該使用 [try_receive](concurrency-namespace-functions.md) 函式，而不是以 `receive` (零) 的超時時間呼叫 `0` ，因為它較有效率，而且不會在發生超時時擲回例外狀況。

如需詳細資訊，請參閱 [訊息傳遞函數](../../../parallel/concrt/message-passing-functions.md)。

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a> run_with_cancellation_token

在指定的取消語彙基元內容中立即和同步地執行函式物件。

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>參數

*_Function*<br/>
將要叫用的函式物件類型。

*_Func*<br/>
要執行的函式物件。 這個物件必須支援具有 void(void) 簽章的函式呼叫運算子。

*_Ct*<br/>
將控制函式物件之隱含取消作業的取消語彙基元。 如果您想要執行函式，而不會從要取消的父工作群組隱含取消，請使用 `cancellation_token::none()`。

### <a name="remarks"></a>備註

函式物件中的所有中斷點都會在 `cancellation_token` 取消時觸發。 如果父項擁有不同的語彙基元或沒有語彙基元，則明確的語彙基元 `_Ct` 會將這個 `_Func` 與父取消隔離。

## <a name="send"></a><a name="send"></a> 發送

同步傳送作業，其會等候直到目標接受或拒絕訊息。

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>參數

*T*<br/>
裝載類型。

*_Trg*<br/>
傳送資料之目標的指標或參考。

*_Data*<br/>
要傳送之資料的參考。

### <a name="return-value"></a>傳回值

**`true`** 如果已接受訊息，則 **`false`** 為，否則為。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [訊息傳遞函數](../../../parallel/concrt/message-passing-functions.md)。

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a> set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>參數

*_Scheduler*<br/>
要設定的環境排程器。

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a> set_task_execution_resources

依據指定的同質性集，限制並行執行階段之內部背景工作執行緒使用的執行資源。

只有在資源管理員建立之前，或在兩個資源管理員存留期之間，才能有效地呼叫這個方法。 只要資源管理員不在引動過程期間，即可多次叫用此函式。 在同質性限制設定之後，直到下次有效呼叫 `set_task_execution_resources` 方法之前，該限制會持續有效。

提供的同質性遮罩不需為處理序同質性遮罩的子集。 您可視需要更新處理序的同質性遮罩。

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>參數

*_ProcessAffinityMask*<br/>
要做為並行執行階段背景工作執行緒之限制的同質性遮罩。 只有在您想要將並行執行階段限制於目前處理器群組的子集時，才在有超過 64 個硬體執行緒的系統上使用這個方法。 一般而言，您應該使用接受群組同質性陣列做為參數的方法版本，以便在擁有超過 64 個硬體執行緒的電腦上限制同質性。

*計數*<br/>
`GROUP_AFFINITY` 參數所指定之陣列中 `_PGroupAffinity` 元素的數目。

*_PGroupAffinity*<br/>
`GROUP_AFFINITY` 元素的陣列。

### <a name="remarks"></a>備註

如果 Resource Manager 存在於叫用時，方法將會擲回 [invalid_operation](invalid-operation-class.md) 例外狀況，而如果指定的親和性會導致一組空的資源，則 [invalid_argument](../../../standard-library/invalid-argument-class.md) 例外狀況。

採用群組同質性陣列做為參數的方法版本只可在執行 Windows 7 (含) 以上版本的作業系統上使用。 否則，就會擲回 [invalid_operation](invalid-operation-class.md) 的例外狀況。

在叫用此方法之後，以程式設計方式修改進程親和性，並不會導致 Resource Manager 重新評估受限制的親和性。 因此，對處理序同質性的所有變更都應該在呼叫這個方法之前進行。

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個 `concurrent_vector` 物件的項目。

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>參數

*T*<br/>
並行向量中儲存之元素的資料類型。

*_Ax*<br/>
並行向量的配置器類型。

*_A*<br/>
其元素要與並行向量交換的並行向量 `_B` 。

*_B*<br/>
提供要交換之元素的並行向量，或其專案要與並行向量的元素交換的向量 `_A` 。

### <a name="remarks"></a>備註

範本函式是在容器類別上特製化的演算法 `concurrent_vector` ，用來執行成員函式 `_A` 。 [concurrent_vector：： swap](concurrent-vector-class.md#swap) ( `_B`) 。 這是編譯器所執行函式樣板部分排序的執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 範本函式的一般版本， `template <class T> void swap(T&, T&)` 在演算法類別中的運作方式是依指派，且是緩慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。

這個方法不是平行存取安全的。 當您呼叫這個方法時，您必須確定任何其他執行緒都不會對任何並行向量執行作業。

## <a name="task_from_exception"></a><a name="task_from_exception"></a> task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>參數

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>傳回值

## <a name="task_from_result"></a><a name="task_from_result"></a> task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>參數

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>傳回值

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a> Trace_agents_register_name

將指定的名稱與 ETW 追蹤的訊息區塊或代理程式產生關聯。

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>參數

*T*<br/>
物件的類型。 這通常是訊息區塊或代理程式。

*_PObject*<br/>
要在追蹤中命名的訊息區塊或代理程式的指標。

*_Name*<br/>
所指物件的名稱。

## <a name="try_receive"></a><a name="try_receive"></a> try_receive

一般嘗試-接收實作，可讓內容尋找來自特定一個來源的資料，並且篩選所接受的值。 如果資料尚未準備好，方法將會傳回 **`false`** 。

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>參數

*T*<br/>
裝載類型

*_Src*<br/>
預期資料的來源指標或參考。

*_value*<br/>
將放置結果之位置的參考。

*_Filter_proc*<br/>
判斷是否應接受訊息的篩選函數。

### <a name="return-value"></a>傳回值

**`bool`** 值，指出是否已在中放置承載 `_value` 。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [訊息傳遞函數](../../../parallel/concrt/message-passing-functions.md)。

## <a name="wait"></a><a name="wait"></a> 等

暫停目前的內容達指定的時間長度。

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>參數

*_Milliseconds*<br/>
目前內容應該暫停的毫秒數。 如果 `_Milliseconds` 參數設定為數值 `0`，則目前內容應該會先執行其他可執行的內容，然後再繼續進行。

### <a name="remarks"></a>備註

如果在並行執行階段排程器內容上呼叫這個方法，排程器將會在基礎資源上尋找要執行的不同內容。 由於排程器是合作性質，因此在指定的毫秒數之後，這個內容不會確實繼續進行。 如果排程器忙於執行其他不能配合排程器的工作，則等候期間可能會是無限期。

## <a name="when_all"></a><a name="when_all"></a> when_all

建立工作，這個工作將會在當做引數提供的所有工作都已順利完成時成功完成。

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
輸入迭代器的類型。

*_Begin*<br/>
合併至所產生工作之項目範圍內的第一個項目位置。

*_End*<br/>
合併至所產生工作之項目範圍外的第一個項目位置。

*_TaskOptions*<br/>
`task_options` 物件。

### <a name="return-value"></a>傳回值

當所有輸入工作都順利完成時，會順利完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作的類型為 **`void`** ，則輸出工作也會是 `task<void>` 。

### <a name="remarks"></a>備註

`when_all` 是未封鎖的函式，會產生 `task` 做為其結果。 不同于 [task：： wait](task-class.md#wait)，您可以放心地在 ASTA (應用程式 STA) 執行緒上的 UWP 應用程式中呼叫此函式。

如果其中一項工作已取消或擲回例外狀況，則傳回的工作會提早完成，而且如果發生例外狀況，則會在您呼叫工作 [：： get](task-class.md#get) 或在該工作時擲回例外狀況（如果發生的話） `task::wait` 。

如需詳細資訊，請參閱工作 [平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

## <a name="when_any"></a><a name="when_any"></a> when_any

建立工作，這個工作會在當做引數提供的所有工作都順利完成時，順利完成。

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>參數

*_Iterator*<br/>
輸入迭代器的類型。

*_Begin*<br/>
合併至所產生工作之項目範圍內的第一個項目位置。

*_End*<br/>
合併至所產生工作之項目範圍外的第一個項目位置。

*_TaskOptions*<br/>
*_CancellationToken*<br/>
取消語彙基元，控制傳回工作的取消作業。 如果未提供取消語彙基元，產生的工作將會收到導致其完成之工作的取消語彙基元。

### <a name="return-value"></a>傳回值

一項工作會在所有輸入工作都順利完成時，順利完成。 如果輸入工作的類型為 `T`，則這個函式的輸出會是 `task<std::pair<T, size_t>>>`，其中配對的第一個項目是完成工作的結果，而第二個項目是已完成工作的索引。 如果輸入工作的類型為 **`void`** ，則輸出為 `task<size_t>` ，其中的結果會是完成工作的索引。

### <a name="remarks"></a>備註

`when_any` 是未封鎖的函式，會產生 `task` 做為其結果。 不同于 [task：： wait](task-class.md#wait)，您可以放心地在 ASTA (應用程式 STA) 執行緒上的 UWP 應用程式中呼叫此函式。

如需詳細資訊，請參閱工作 [平行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
