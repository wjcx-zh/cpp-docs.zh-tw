---
title: concurrency 命名空間函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66cf776e02d286b04c4fe9338d74d6a9db196a68
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="concurrency-namespace-functions"></a>concurrency 命名空間函式
||||  
|-|-|-|  
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|  
|[EnableTracing](#enabletracing)|[可用](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|  
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[傳送](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[wait](#wait)|  
|[when_all](#when_all)|[when_any](#when_any)|  
  
##  <a name="alloc"></a>  Alloc  
 會透過並行執行階段的快取子配置器指定的大小，來配置記憶體區塊。  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>參數  
 `_NumBytes`  
 要配置的記憶體的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 新配置的記憶體指標。  
  
### <a name="remarks"></a>備註  
 哪些應用程式中的案例可能受益於使用快取子配置器的詳細資訊，請參閱[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
##  <a name="asend"></a>  asend  
 非同步傳送作業，會排程工作將資料傳播到目標區塊。  
  
```
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
 `T`  
 要傳送的資料類型。  
  
 `_Trg`  
 指標或參考的資料會傳送的目標。  
  
 `_Data`  
 傳送資料的參考。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已接受，則方法會傳回，`false`否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[訊息傳遞函式](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="cancel_current_task"></a>  cancel_current_task  
 取消目前執行的工作。 這個函式可以從工作主體內呼叫，以中止工作執行並導致它進入 `canceled` 狀態。  
  
 如果不是在 `task` 的主體中，這就不是支援呼叫這個函式的情況。 這樣做會在應用程式中導致未定義的行為，例如當機或停止回應。  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>  clear  
 清除並行佇列，破壞任何目前項目加入佇列。 這個方法不是並行安全。  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>參數  
 `T`  
 `_Ax`  
  
##  <a name="create_async"></a>  create_async  
 以使用者提供的 Lambda 或函式物件為基礎，建立 Windows 執行階段非同步建構。 根據傳遞至方法的 Lambda 簽章，`create_async` 的傳回類型是下列其中一個：`IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^`。  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 `_Func`  
 從中建立 Windows 執行階段非同步建構的 Lambda 或函式物件。  
  
### <a name="return-value"></a>傳回值  
 由 IAsyncAction 表示的非同步建構 ^，IAsyncActionWithProgress\<TProgress > ^、 Iasyncoperation<tresult>\<TResult > ^，或 Iasyncoperationwithprogress<tresult\<Iasyncoperationwithprogress<tresult，TProgress > ^。 傳回的介面依賴傳遞至函式的 Lambda 簽章。  
  
### <a name="remarks"></a>備註  
 Lambda 的傳回型別決定建構是動作或作業。  
  
 傳回 void 的 Lambda 造成動作的建立。 傳回屬於 `TResult` 類型之結果的 Lambda 會造成 TResult 作業的建立。  
  
 Lambda 可能也會傳回 `task<TResult>`，將非同步工作封裝在本身內或是表示非同步工作的工作鏈結的接續作業。 在這種情況下，Lambda 本身是內嵌執行，因為工作是非同步執行的工作，而且 Lambda 的傳回類型會解除包裝以產生 `create_async` 所傳回的非同步建構。 這表示，lambda 會傳回工作\<void > 會造成的動作，並傳回工作的 lambda 建立\<TResult > 會導致 TResult 作業的建立。  
  
 Lambda 可以接受零個、一個或兩個引數。 有效的引數為 `progress_reporter<TProgress>` 和 `cancellation_token`，兩者都使用時依此順序。 沒有引數的 Lambda 會導致建立沒有進度報告功能的非同步建構。 Lambda 採用 progress_reporter\<TProgress > 會導致`create_async`要傳回的非同步建構，它會報告 TProgress 類型的進度，每次`report`呼叫 progress_reporter 物件的方法。 接受 cancellation_token 的 Lambda 可能使用該語彙基元來檢查取消的狀態，或是將語彙基元傳遞給所建立的工作，讓非同步建構的取消導致取消這些工作。  
  
 如果 lambda 或函式物件的主體傳回結果 (而非\<TResult >)，將會以非同步方式執行 task<tresult>，MTA 的執行階段的工作內容中隱含為其建立處理序內。 `IAsyncInfo::Cancel` 方法會導致取消隱含工作。  
  
 如果 Lambda 的主體傳回工作，則 Lambda 會內嵌執行，而且藉由宣告 Lambda 接受屬於類型 `cancellation_token` 的引數，您可以觸發任何工作的取消作業，這些工作是您建立工作時，透過傳入該語彙基元，在 Lambda 建立的。 您也可以在語彙基元使用 `register_callback` 方法，使執行階段在您在非同步作業或產生的動作呼叫 `IAsyncInfo::Cancel` 時叫用回呼。  
  
 此函式只適用於 Windows 執行階段應用程式。  
  
##  <a name="createresourcemanager"></a>  CreateResourceManager  
 傳回代表並行執行階段資源管理員單一執行個體的介面。 資源管理員會負責將資源指派給想要與彼此相互合作的排程器。  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>傳回值  
 `IResourceManager` 介面。  
  
### <a name="remarks"></a>備註  
 這個方法的多個後續呼叫會傳回相同的資源管理員的執行個體。 每次呼叫該方法會遞增參考計數在資源管理員，且必須符合呼叫[iresourcemanager:: Release](http://msdn.microsoft.com/en-us/5d1356ec-fbd3-4284-a361-1e9e20bbb522)方法完成您的排程器與資源管理員進行通訊。  
  
 [unsupported_os](unsupported-os-class.md)如果作業系統不支援之並行執行階段會擲回。  
  
##  <a name="create_task"></a>  create_task  
 建立 PPL[工作](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f)物件。 您可以在任何會使用工作建構函式的地方使用 `create_task`。 這主要是為了方便起見而提供，因為它允許在建立工作時使用 `auto` 關鍵字。  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 從中要建構工作的參數的類型。  
  
 `_ReturnType`  
 `_Param`  
 從中要建構工作的參數。 這可能是 lambda 或函式的物件，`task_completion_event`物件、 不同`task`的物件或如果您在 UWP 應用程式中使用工作 Windows::Foundation::IAsyncInfo 介面。  
  
 `_TaskOptions`  
 `_Task`  
  
### <a name="return-value"></a>傳回值  
 新的工作類型的`T`，也就是從推斷`_Param`。  
  
### <a name="remarks"></a>備註  
 第一個多載的行為類似工作建構函式採用單一參數。  
  
 第二個多載會將提供與新建立之工作的取消語彙基元。 如果您使用這個多載您不允許將不同`task`物件做為第一個參數。  
  
 傳回工作的類型是從第一個參數推斷函式。 如果`_Param`是`task_completion_event<T>`、 `task<T>`，或函式會傳回其中一個型別`T`或`task<T>`，建立之工作的類型是`task<T>`。  
  
 在 UWP 應用程式中，如果`_Param`的型別 Windows::Foundation::IAsyncOperation\<T > ^ 或 Windows::Foundation::IAsyncOperationWithProgress\<T、 P > ^，或傳回這些型別的函式，建立的工作，都屬於型別`task<T>`。 如果`_Param`的型別 Windows::Foundation::IAsyncAction ^ 或 Windows::Foundation::IAsyncActionWithProgress\<P > ^，或傳回這些型別的函式，建立的工作將會有輸入`task<void>`。  
  
##  <a name="disabletracing"></a>  DisableTracing  
 停用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已移除註冊而被取代。  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>傳回值  
 如果正確地停用追蹤，`S_OK`傳回。 如果先前未啟始追蹤，則會傳回 `E_NOT_STARTED`  
  
##  <a name="enabletracing"></a>  EnableTracing  
 啟用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已開啟而被取代。  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>傳回值  
 如果追蹤已正確初始化，請`S_OK`會傳回，否則`E_NOT_STARTED`傳回。  
  
##  <a name="free"></a>  Free  
 釋放先前由 `Alloc` 方法配置的記憶體區塊至並行執行階段的快取子配置器。  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>參數  
 `_PAllocation`  
 先前所配置的記憶體指標`Alloc`方法，也就是被釋放。 如果參數`_PAllocation`設定為值`NULL`，這個方法會忽略它並立即傳回。  
  
### <a name="remarks"></a>備註  
 哪些應用程式中的案例可能受益於使用快取子配置器的詳細資訊，請參閱[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="getexecutioncontextid"></a>  GetExecutionContextId  
 傳回可指派給實作 `IExecutionContext` 介面之執行內容的唯一識別碼。  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>傳回值  
 執行內容的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 使用這個方法來取得執行內容的識別項，才能傳遞`IExecutionContext`做為任何提供資源管理員的方法參數的介面。  
  
##  <a name="getosversion"></a>  GetOSVersion  
 傳回作業系統版本。  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>傳回值  
 列舉的值，表示作業系統。  
  
### <a name="remarks"></a>備註  
 [unsupported_os](unsupported-os-class.md)如果作業系統不支援之並行執行階段會擲回。  
  
##  <a name="getprocessorcount"></a>  GetProcessorCount  
 傳回基礎系統上的硬體執行緒數目。  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>傳回值  
 硬體執行緒數目。  
  
### <a name="remarks"></a>備註  
 [unsupported_os](unsupported-os-class.md)如果作業系統不支援之並行執行階段會擲回。  
  
##  <a name="getprocessornodecount"></a>  GetProcessorNodeCount  
 傳回基礎系統上的 NUMA 節點或處理器套件數目。  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>傳回值  
 NUMA 節點或處理器套件數目。  
  
### <a name="remarks"></a>備註  
 如果系統包含多個 NUMA 節點與處理器封裝，傳回 NUMA 節點數目，否則會傳回處理器套件數目。  
  
 [unsupported_os](unsupported-os-class.md)如果作業系統不支援之並行執行階段會擲回。  
  
##  <a name="getschedulerid"></a>  GetSchedulerId  
 傳回可指派給實作 `IScheduler` 介面之排程器的唯一識別碼。  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>傳回值  
 排程器的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 使用這個方法來取得您的排程器識別項之前先`IScheduler`做為任何提供資源管理員的方法參數的介面。  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>參數  
 `T`  
 `_Ax`  
 `_I`  
 `first`  
 `last`  
  
##  <a name="interruption_point"></a>  interruption_point  
 建立取消的中斷點。 如果這個函式呼叫的內容正在取消，則會擲出中止目前執行之平行工作執行的內部例外狀況。 如果取消不在進行中，函式不會執行任何動作。  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>備註  
 您不應該攔截 `interruption_point()` 函式擲回的內部取消例外狀況。 例外狀況會由執行階段攔截並處理，而攔截它可能會造成程式行為異常。  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling  
 傳回指示，以說明目前正以內嵌方式在目前內容上執行的工作群組是否正在取消 (或即將取消)。 請注意，如果目前沒有任何工作群組以內嵌方式在目前的內容上執行，會傳回 `false`。  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>傳回值  
 `true` 正在取消目前正在執行的工作群組，如果`false`否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[取消](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)。  
  
##  <a name="make_choice"></a>  make_choice  
 從選擇性的 `choice` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。  
  
```
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
 `T1`  
 第一個來源訊息區塊類型。  
  
 `T2`  
 第二個來源訊息區塊類型。  
  
 `_PScheduler`  
 `Scheduler` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。  
  
 `_Item1`  
 第一個來源。  
  
 `_Item2`  
 第二個來源。  
  
 `_Items`  
 其他來源。  
  
 `_PScheduleGroup`  
 `ScheduleGroup` 物件，在其內會排定 `choice` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="return-value"></a>傳回值  
 有兩個或多個輸入來源的 `choice` 訊息區塊。  
  
##  <a name="make_greedy_join"></a>  make_greedy_join  
 從選擇性的 `greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。  
  
```
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
 `T1`  
 第一個來源訊息區塊類型。  
  
 `T2`  
 第二個來源訊息區塊類型。  
  
 `_PScheduler`  
 `Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。  
  
 `_Item1`  
 第一個來源。  
  
 `_Item2`  
 第二個來源。  
  
 `_Items`  
 其他來源。  
  
 `_PScheduleGroup`  
 `ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="return-value"></a>傳回值  
 有兩個或多個輸入來源的 `greedy multitype_join` 訊息區塊。  
  
##  <a name="make_join"></a>  make_join  
 從選擇性的 `non_greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。  
  
```
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
 `T1`  
 第一個來源訊息區塊類型。  
  
 `T2`  
 第二個來源訊息區塊類型。  
  
 `_PScheduler`  
 `Scheduler` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。  
  
 `_Item1`  
 第一個來源。  
  
 `_Item2`  
 第二個來源。  
  
 `_Items`  
 其他來源。  
  
 `_PScheduleGroup`  
 `ScheduleGroup` 物件，在其內會排定 `multitype_join` 傳訊區塊的傳播工作。 所使用的 `Scheduler` 物件由排程群組所隱含。  
  
### <a name="return-value"></a>傳回值  
 有兩個或多個輸入來源的 `non_greedy multitype_join` 訊息區塊。  
  
##  <a name="make_task"></a>  make_task  
 建立 `task_handle` 物件的 Factory 方法。  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用以執行該工作所表示的函式物件類型`task_handle`物件。  
  
 `_Func`  
 將要叫用以執行該工作所表示的函式`task_handle`物件。 這可能是 lambda 函式，函式指標，或任何物件的支援版本的函式呼叫運算子與簽章`void operator()()`。  
  
### <a name="return-value"></a>傳回值  
 `task_handle` 物件。  
  
### <a name="remarks"></a>備註  
 此函式時，您必須建立`task_handle`物件與 lambda 運算式，因為它可讓您建立的物件，而不需要知道的 lambda 函式，則為 true 的類型。  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort  
 將在指定範圍中的項目排列成非遞減順序，或是依據二元述詞指定的順序準則以平行方式排列。 這個函式語意與 `std::sort` 類似：皆是以比較為基礎、不穩定、就地排序的；差別為它需要 `O(n)` 額外的空間，且必須預設初始化需排序的項目。  
  
```
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
 `_Random_iterator`  
 輸入範圍的迭代器類型。  
  
 `_Allocator`  
 C + + 標準程式庫相容的記憶體配置器類型。  
  
 `_Function`  
 二元比較子類型。  
  
 `_Begin`  
 隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。  
  
 `_End`  
 隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。  
  
 `_Alloc`  
 C + + 標準程式庫相容的記憶體配置器的執行個體。  
  
 `_Func`  
 使用者定義的述詞函式物件，用來定義順序中後續項目應符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 `true`，不符合時則傳回 `false`。 這個比較子函式必須對序列中項目的配對強制執行嚴格的弱式順序。  
  
 `_Chunk_size`  
 要分割成兩個進行並行執行的最小區塊大小。  
  
### <a name="remarks"></a>備註  
 所有多載必須`n * sizeof(T)`額外的空間，其中`n`是要排序的項目數和`T`的元素類型。 在大部分情況下 parallel_buffered_sort 會透過顯示的效能已提升[parallel_sort](concurrency-namespace-functions.md)，而且您應該使用它透過 parallel_sort 如果您有可用的記憶體。  
  
 如果您未提供二元比較子`std::less`做為預設，這需要的項目類型，可提供操作員`operator<()`。  
  
 如果您未提供使用配置器類型或執行個體，c + + 標準程式庫的記憶體配置器`std::allocator<T>`用來配置的緩衝區。  
  
 演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性的引數 `_Chunk_size` 可用來對演算法指出，它應該依序處理大小 < `_Chunk_size` 的區塊。  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for` 會逐一查看某個範圍的索引，並以平行方式在每個反覆項目上執行使用者提供的函式。  
  
```
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
 `_Index_type`  
 反覆項目所使用的索引類型。  
  
 `_Function`  
 每個反覆項目會執行函式的類型。  
  
 `_Partitioner`  
 用來分割提供的範圍的 partitioner 型別。  
  
 `first`  
 要包含在反覆項目中第一個索引。  
  
 `last`  
 索引一個過去的反覆項目中包含的最後一個索引。  
  
 `_Step`  
 值，用來從時，逐步`first`至`last`。 在步驟必須是正數。 [invalid_argument](../../../standard-library/invalid-argument-class.md)的步驟是小於 1，則會擲回。  
  
 `_Func`  
 要在每個反覆項目執行的函式。 這可能是 lambda 運算式、 函式指標，或任何物件的支援版本的函式呼叫運算子與簽章`void operator()(_Index_type)`。  
  
 `_Part`  
 Partitioner 物件的參考。 引數可以是其中一個`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_partitioner](simple-partitioner-class.md) `&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)物件，則必須為非 const 左值參考。參考，使演算法可以儲存為未來的迴圈，以重複使用的狀態。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[平行演算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each` 會平行套用指定的函式到範圍內的每個項目。 在語意上，它相當於 `std` 命名空間中的 `for_each` 函式，但項目的反覆項目會平行執行，而且不會指定反覆項目的順序。 `_Func` 引數必須支援 `operator()(T)` 形式的函式呼叫運算子，其中 `T` 參數是要逐一查看之容器的項目類型。  
  
```
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
 `_Iterator`  
 用來反覆查看容器的迭代器類型。  
  
 `_Function`  
 將會套用到每個項目範圍內的函式類型。  
  
 `_Partitioner`  
 `first`  
 迭代器定址的第一個項目要包含在平行反覆項目中。  
  
 `last`  
 迭代器定址最後一個項目的後面一個位置包含平行反覆項目中。  
  
 `_Func`  
 使用者定義函式物件套用到範圍中每個項目。  
  
 `_Part`  
 Partitioner 物件的參考。 引數可以是其中一個`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_partitioner](simple-partitioner-class.md) `&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)物件，則必須為非 const 左值參考。參考，使演算法可以儲存為未來的迴圈，以重複使用的狀態。  
  
### <a name="remarks"></a>備註  
 [auto_partitioner](auto-partitioner-class.md)將用於不含明確 partitioner 的多載。  
  
 對於不支援隨機迭代器存取，只[auto_partitioner](auto-partitioner-class.md)支援。  
  
 如需詳細資訊，請參閱[平行演算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_invoke"></a>  parallel_invoke  
 平行執行提供作為參數的函式物件，並加以封鎖直到完成執行為止。 函式物件可能是 Lambda 運算式、函式指標，或是支援函式呼叫運算子與簽章 `void operator()()` 版本的任何物件。  
  
```
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
 `_Function1`  
 若要以平行方式執行的第一個函式物件類型。  
  
 `_Function2`  
 若要以平行方式執行的第二個函式物件類型。  
  
 `_Function3`  
 若要以平行方式執行的第三個函式物件類型。  
  
 `_Function4`  
 若要以平行方式執行的第四個函式物件類型。  
  
 `_Function5`  
 若要以平行方式執行的第五個函式物件類型。  
  
 `_Function6`  
 若要以平行方式執行的第六個函式物件類型。  
  
 `_Function7`  
 若要以平行方式執行的第七個函式物件類型。  
  
 `_Function8`  
 若要以平行方式執行的第八個函式物件類型。  
  
 `_Function9`  
 若要以平行方式執行的第九個函式物件類型。  
  
 `_Function10`  
 若要以平行方式執行的第十個函式物件類型。  
  
 `_Func1`  
 要平行執行的第一個函式物件。  
  
 `_Func2`  
 要平行執行的第二個函式物件。  
  
 `_Func3`  
 要平行執行的第三個函式物件。  
  
 `_Func4`  
 要平行執行的第四個函式物件。  
  
 `_Func5`  
 要平行執行的第五個函式物件。  
  
 `_Func6`  
 要平行執行的第六個函式物件。  
  
 `_Func7`  
 要平行執行的第七個函式物件。  
  
 `_Func8`  
 要平行執行的第八個函式物件。  
  
 `_Func9`  
 要平行執行的第九個函式物件。  
  
 `_Func10`  
 要平行執行的第十個函式物件。  
  
### <a name="remarks"></a>備註  
 請注意一或多個函式物件提供的參數可能會執行內嵌呼叫端內容上。  
  
 如果一或多個函式物件當做參數傳遞給此函式擲回例外狀況，執行階段會選取其選擇的一個這類例外狀況，傳播超出呼叫`parallel_invoke`。  
  
 如需詳細資訊，請參閱[平行演算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort  
 使用基數排序演算法，將指定範圍內的項目排列成非遞減順序。 這是一個穩定的排序函式，其需要可將項目排序成不帶正負號的整數機碼的投影函式。 要排序的項目都必須進行預設初始化。  
  
```
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
 `_Random_iterator`  
 輸入範圍的迭代器類型。  
  
 `_Allocator`  
 C + + 標準程式庫相容的記憶體配置器類型。  
  
 `_Function`  
 投影函式的類型。  
  
 `_Begin`  
 隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。  
  
 `_End`  
 隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。  
  
 `_Alloc`  
 C + + 標準程式庫相容的記憶體配置器的執行個體。  
  
 `_Proj_func`  
 使用者定義的投影函式物件，將元素轉換成整數的值。  
  
 `_Chunk_size`  
 要分割成兩個進行並行執行的最小區塊大小。  
  
### <a name="remarks"></a>備註  
 所有多載必須`n * sizeof(T)`額外的空間，其中`n`是要排序的項目數和`T`的元素類型。 一元投影仿函式的簽章`I _Proj_func(T)`才能傳回索引鍵時指定新項目，其中`T`是項目類型和`I`是不帶正負號的整數式型別。  
  
 如果您未提供投影函式，只會傳回元素的預設投影函式用於整數類資料類型。 此函式，將無法編譯如果項目不是整數類型的投影函式不存在。  
  
 如果您未提供使用配置器類型或執行個體，c + + 標準程式庫的記憶體配置器`std::allocator<T>`用來配置的緩衝區。  
  
 演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性的引數 `_Chunk_size` 可用來對演算法指出，它應該依序處理大小 < `_Chunk_size` 的區塊。  
  
##  <a name="parallel_reduce"></a>  parallel_reduce  
 以平行方式，透過計算後繼元素的部分總和來計算在一定範圍內所有項目的總和，或是計算部分後繼結果 (取得方式是使用指定的二進位運算而非總和運算得出) 的結果。 `parallel_reduce` 語意與 `std::accumulate` 類似；不同的是，它需要關聯的二進位運算，而且需要識別值而不是初始值。  
  
```
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
 `_Forward_iterator`  
 輸入範圍的迭代器類型。  
  
 `_Sym_reduce_fun`  
 對稱的減少函式的類型。 這必須是函式具有類型簽章`_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`_Reduce_type 所在相同的識別類型以及減少的結果型別。 第三個多載，這應該是一致的輸出型別與`_Range_reduce_fun`。  
  
 `_Reduce_type`  
 型別，輸入將會減少，這可能會從輸入項目的型別不同。 識別值與傳回值將會有這種類型。  
  
 `_Range_reduce_fun`  
 範圍減少函式的類型。 這必須是函式具有類型簽章`_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`，_Reduce_type 是相同的識別類型以及減少的結果型別。  
  
 `_Begin`  
 輸入迭代器定址範圍中的第一個元素會減少。  
  
 `_End`  
 輸入迭代器是降低範圍中的最後一個項目之外的一個位置的項目定址。  
  
 `_Identity`  
 識別值`_Identity`減少的結果型別相同型別的以及`value_type`的第一個和第二個多載的迭代器。 第三個多載，身分識別值必須具有減少的結果型別相同的型別，但可以不同於`value_type`迭代器。 它必須有適當的值，範圍削減運算子`_Range_fun`，當套用至類型的單一項目範圍`value_type`識別值的行為類似的類型值的型別轉換和`value_type`身分識別類型。  
  
 `_Sym_fun`  
 將使用中的第二個降低對稱函式。 如需詳細資訊，請參閱 < 備註 >。  
  
 `_Range_fun`  
 降低的第一個階段，將使用的函式。 如需詳細資訊，請參閱 < 備註 >。  
  
### <a name="return-value"></a>傳回值  
 減少的結果。  
  
### <a name="remarks"></a>備註  
 若要執行的平行降低，函式會將範圍分割成區塊根據基礎排程器的可用工作者數目。 降低發生在兩個階段、 第一個階段中執行每個區塊中, 減少和第二個階段執行每個區塊的部分結果之間減少。  
  
 第一個多載的所需的迭代器`value_type`， `T`，是相同的識別值型別，以及減少的結果型別。 項目型別 T 必須提供運算子`T T::operator + (T)`以減少每個區塊中的項目。 在第二個階段使用相同的運算子。  
  
 第二個多載也需要的迭代器的`value_type`做為身分識別的實值型別，以及減少的結果型別必須相同。 提供的二進位運算子`_Sym_fun`用於這兩個減少階段中，身分識別值與第一個階段的起始值。  
  
 第三個多載中，身分識別值類型必須相同減少的結果型別，但迭代器的`value_type`可能都不同。 範圍減少函式`_Range_fun`做為起始的值，並將二元函式第一個階段中使用的識別值用於`_Sym_reduce_fun`套用至子中的第二個階段的結果。  
  
##  <a name="parallel_sort"></a>  parallel_sort  
 將在指定範圍中的項目排列成非遞減順序，或是依據二元述詞指定的順序準則以平行方式排列。 這個函式語意與 `std::sort` 類似，皆是以比較為基礎、不穩定、就地排序的。  
  
```
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
 `_Random_iterator`  
 輸入範圍的迭代器類型。  
  
 `_Function`  
 二元比較子仿函數 (functor) 的類型。  
  
 `_Begin`  
 隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。  
  
 `_End`  
 隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。  
  
 `_Func`  
 使用者定義的述詞函式物件，用來定義順序中後續項目應符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 `true`，不符合時則傳回 `false`。 這個比較子函式必須對序列中項目的配對強制執行嚴格的弱式順序。  
  
 `_Chunk_size`  
 要分割成兩個進行並行執行的最小區塊大小。  
  
### <a name="remarks"></a>備註  
 第一個多載會使用二元比較子 `std::less`。  
  
 第二個多載會使用提供的二元比較子，該比較子應具有 `bool _Func(T, T)` 簽章，其中 `T` 是輸入範圍中項目的類型。  
  
 演算法會將輸入範圍分成兩個區塊，接著在將每個區塊分成兩個子區塊以進行平行執行。 選擇性的引數 `_Chunk_size` 可用來對演算法指出，它應該依序處理大小 < `_Chunk_size` 的區塊。  
  
##  <a name="parallel_transform"></a>  parallel_transform  
 以平行方式，將指定的函式物件套用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。 此函式在語意上等於 `std::transform`。  
  
```
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
 `_Input_iterator1`  
 第一個或唯一一個輸入迭代器的類型。  
  
 `_Output_iterator`  
 輸出迭代器類型。  
  
 `_Unary_operator`  
 在輸入範圍內的每個項目上執行的一元仿函數 (functor) 類型。  
  
 `_Input_iterator2`  
 第二個輸入迭代器的類型。  
  
 `_Binary_operator`  
 在兩個來源範圍的項目上成對執行的二元仿函數 (functor) 類型。  
  
 `_Partitioner`  
 `first1`  
 輸入迭代器，用於定址在第一個或唯一一個來源範圍上執行之第一個項目的位置。  
  
 `last1`  
 輸入迭代器，用於定址超過要在第一個或唯一一個來源範圍中執行之最後一個項目的第一個位置。  
  
 `_Result`  
 輸出迭代器，用於定址目的範圍中第一個項目的位置。  
  
 `_Unary_op`  
 套用至來源範圍中每個項目的使用者定義一元函式物件。  
  
 `_Part`  
 Partitioner 物件的參考。 引數可以是其中一個`const` [auto_partitioner](auto-partitioner-class.md)`&`， `const` [static_partitioner](static-partitioner-class.md)`&`， `const` [simple_partitioner](simple-partitioner-class.md) `&`或[affinity_partitioner](affinity-partitioner-class.md) `&`如果[affinity_partitioner](affinity-partitioner-class.md)物件，則必須為非 const 左值參考。參考，使演算法可以儲存為未來的迴圈，以重複使用的狀態。  
  
 `first2`  
 輸入迭代器，用於定址第二個來源範圍中要執行之第一個項目的位置。  
  
 `_Binary_op`  
 使用者定義的二元函式物件，它會以正向順序成對套用至兩個來源範圍。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器，用於定址超過接收函式物件所轉換之輸出項目的目的範圍中最後一個項目的第一個位置。  
  
### <a name="remarks"></a>備註  
 [auto_partitioner](auto-partitioner-class.md)將用於不含明確 partitioner 引數的多載。  
  
 對於不支援隨機迭代器存取，只[auto_partitioner](auto-partitioner-class.md)支援。  
  
 採用 `_Unary_op` 引數的多載會透過將一元仿函數套用至輸出範圍中的每個項目，將輸入範圍轉換成輸出範圍。 `_Unary_op` 必須支援具有 `operator()(T)` 簽章的函式呼叫運算子，其中 `T` 是反覆查看之範圍的實值類型。  
  
 採用 `_Binary_op` 引數的多載會透過將二元仿函數套用至第一個輸入範圍的某一個項目和第二個輸入範圍的某一個項目，將兩個輸入範圍轉換成輸出範圍。 `_Binary_op` 必須支援具有 `operator()(T, U)` 簽章的函式呼叫運算子，其中 `T`、`U` 為兩個輸入迭代器的實值類型。  
  
 如需詳細資訊，請參閱[平行演算法](../../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="receive"></a>  receive  
 一般接收實作，可讓內容等候來自一個來源的資料，並且篩選所接受的值。  
  
```
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
 `T`  
 裝載類型。  
  
 `_Src`  
 指標或參考的預期資料的來源。  
  
 `_Timeout`  
 最大時間，此方法應的資料，以毫秒為單位。  
  
 `_Filter_proc`  
 篩選函數用來決定是否應該接受訊息。  
  
### <a name="return-value"></a>傳回值  
 來源的裝載類型的值。  
  
### <a name="remarks"></a>備註  
 如果參數`_Timeout`常數以外的值`COOPERATIVE_TIMEOUT_INFINITE`，例外狀況[operation_timed_out](operation-timed-out-class.md)如果指定的時間量到期之前收到訊息時，會擲回。 如果您想為零長度逾時，您應該使用[try_receive](concurrency-namespace-functions.md)函式，而不是呼叫`receive`逾時值為`0`（零），因為它會更有效率，而且不會擲回例外狀況上逾時。  
  
 如需詳細資訊，請參閱[訊息傳遞函式](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token  
 在指定的取消語彙基元內容中立即和同步地執行函式物件。  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 將要叫用的函式物件類型。  
  
 `_Func`  
 要執行的函式物件。 這個物件必須支援具有 void(void) 簽章的函式呼叫運算子。  
  
 `_Ct`  
 將控制函式物件之隱含取消作業的取消語彙基元。 如果您想要執行函式，而不會從要取消的父工作群組隱含取消，請使用 `cancellation_token::none()`。  
  
### <a name="remarks"></a>備註  
 函式物件中的所有中斷點都會在 `cancellation_token` 取消時觸發。 如果父項擁有不同的語彙基元或沒有語彙基元，則明確的語彙基元 `_Ct` 會將這個 `_Func` 與父取消隔離。  
  
##  <a name="send"></a>  send  
 同步傳送作業，其會等候直到目標接受或拒絕訊息。  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 裝載類型。  
  
 `_Trg`  
 指標或參考的資料會傳送的目標。  
  
 `_Data`  
 傳送資料的參考。  
  
### <a name="return-value"></a>傳回值  
 `true` 如果訊息已接受，`false`否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[訊息傳遞函式](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>參數  
 `_Scheduler`  
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources  
 依據指定的同質性集，限制並行執行階段之內部背景工作執行緒使用的執行資源。  
  
 只有在資源管理員建立之前，或在兩個資源管理員存留期之間，才能有效地呼叫這個方法。 只要資源管理員不在引動過程期間，即可多次叫用此函式。 在同質性限制設定之後，直到下次有效呼叫 `set_task_execution_resources` 方法之前，該限制會持續有效。
  
  
 提供的同質性遮罩不需為處理序同質性遮罩的子集。 您可視需要更新處理序的同質性遮罩。  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>參數  
 `_ProcessAffinityMask`  
 要做為並行執行階段背景工作執行緒之限制的同質性遮罩。 只有在您想要將並行執行階段限制於目前處理器群組的子集時，才在有超過 64 個硬體執行緒的系統上使用這個方法。 一般而言，您應該使用接受群組同質性陣列做為參數的方法版本，以便在擁有超過 64 個硬體執行緒的電腦上限制同質性。  
  
 `count`  
 `GROUP_AFFINITY` 參數所指定之陣列中 `_PGroupAffinity` 元素的數目。  
  
 `_PGroupAffinity`  
 `GROUP_AFFINITY` 元素的陣列。  
  
### <a name="remarks"></a>備註  
 方法會擲回[invalid_operation](invalid-operation-class.md)例外狀況是否存在時，它會叫用，資源管理員和[invalid_argument](../../../standard-library/invalid-argument-class.md)如果親和性在空的集合中指定結果的例外狀況資源。  
  
 採用群組同質性陣列做為參數的方法版本只可在執行 Windows 7 (含) 以上版本的作業系統上使用。 否則， [invalid_operation](invalid-operation-class.md)擲回例外狀況。  
  
 在叫用這個方法之後以程式設計的方式修改處理序同質性，並不會造成資源管理員重新評估做為限制的同質性。 因此，對處理序同質性的所有變更都應該在呼叫這個方法之前進行。  
  
##  <a name="swap"></a>  swap  
 交換兩個 `concurrent_vector` 物件的項目。  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 並行向量中儲存的項目資料類型。  
  
 `_Ax`  
 並行向量的配置器類型。  
  
 `_A`  
 並行向量，其元素要與並行向量交換`_B`。  
  
 `_B`  
 並行向量提供待交換，項目或其項目要與並行向量交換的向量`_A`。  
  
### <a name="remarks"></a>備註  
 樣板函式是演算法特製化的容器類別`concurrent_vector`執行成員函式`_A`。 [concurrent_vector:: swap](concurrent-vector-class.md#swap)( `_B`)。 這是編譯器所執行函式樣板部分排序的執行個體。 當樣板與函式呼叫不是唯一配對，而使得樣板函式多載時，編譯器會選取最特製化的樣板函式版本。 樣板函式的一般版本`template <class T> void swap(T&, T&)`，演算法中類別的運作方式是指派和很慢的作業。 每個容器中的特製化版本運作速度會更快，因為它可以與容器類別的內部表示法一起運作。  
  
 這個方法不是並行安全。 您必須確定沒有其他執行緒正在執行的並行向量的任何作業，當您呼叫這個方法。  
  
##  <a name="task_from_exception"></a>  task_from_exception  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>參數  
 `_TaskType`  
 `_ExType`  
 `_Exception`  
 `_TaskOptions`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="task_from_result"></a>  task_from_result  
  
```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>參數  
 `T`  
 `_Param`  
 `_TaskOptions`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name  
 將指定的名稱與 ETW 追蹤的訊息區塊或代理程式產生關聯。  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>參數  
 `T`  
 物件的類型。 這通常是訊息區塊或代理程式。  
  
 `_PObject`  
 要在追蹤中命名的訊息區塊或代理程式的指標。  
  
 `_Name`  
 所指物件的名稱。  
  
##  <a name="try_receive"></a>  try_receive  
 一般嘗試-接收實作，可讓內容尋找來自特定一個來源的資料，並且篩選所接受的值。 如果資料還沒準備好，方法會傳回 false。  
  
``` 
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
 `T`  
 裝載類型  
  
 `_Src`  
 指標或參考的預期資料的來源。  
  
 `_value`  
 結果放置的位置參考。  
  
 `_Filter_proc`  
 篩選函數用來決定是否應該接受訊息。  
  
### <a name="return-value"></a>傳回值  
 A`bool`值，指出是否裝載被放在`_value`。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[訊息傳遞函式](../../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="wait"></a>  等候  
 暫停目前的內容達指定的時間長度。  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>參數  
 `_Milliseconds`  
 目前內容應該暫停的毫秒數。 如果 `_Milliseconds` 參數設定為數值 `0`，則目前內容應該會先執行其他可執行的內容，然後再繼續進行。  
  
### <a name="remarks"></a>備註  
 並行執行階段排程器內容上呼叫此方法時，如果排程器會尋找基礎資源上執行不同的內容。 由於排程器是合作性質，因此在指定的毫秒數之後，這個內容不會確實繼續進行。 如果排程器忙於執行其他不能配合排程器的工作，則等候期間可能會是無限期。  
  
##  <a name="when_all"></a>  when_all  
 建立工作，這個工作將會在當做引數提供的所有工作都已順利完成時成功完成。  
  
```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) -> 
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```   
  
### <a name="parameters"></a>參數  
 `_Iterator`  
 輸入迭代器的類型。  
  
 `_Begin`  
 合併至所產生工作之項目範圍內的第一個項目位置。  
  
 `_End`  
 合併至所產生工作之項目範圍外的第一個項目位置。  
  
 `_TaskOptions`  
  
### <a name="return-value"></a>傳回值  
 在所有輸入工作都順利完成時會成功完成的工作。 如果輸入工作屬於類型 `T`，此函式的輸出將會是 `task<std::vector<T>>`。 如果輸入工作屬於類型 `void`，則輸出工作也會是 `task<void>`。  
  
### <a name="remarks"></a>備註  
 `when_all` 是未封鎖的函式，會產生 `task` 做為其結果。 不同於[task:: wait](task-class.md#wait)，您可以放心在 ASTA (應用程式 STA) 執行緒上的 UWP 應用程式呼叫此函式。  
  
 如果其中一項工作取消或擲回例外狀況，則傳回的工作會提早完成，已取消的狀態，而且例外狀況，如果其中有發生，會擲回您呼叫[task:: get](task-class.md#get)或`task::wait`於該工作。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
##  <a name="when_any"></a>  when_any  
 建立工作，當成引數來提供的任何工作順利完成時，此工作就會順利成功。  
  
```
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
 `_Iterator`  
 輸入迭代器的類型。  
  
 `_Begin`  
 合併至所產生工作之項目範圍內的第一個項目位置。  
  
 `_End`  
 合併至所產生工作之項目範圍外的第一個項目位置。  
  
 `_TaskOptions`  
 `_CancellationToken`  
 取消語彙基元，控制傳回工作的取消作業。 如果未提供取消語彙基元，產生的工作將會收到導致其完成之工作的取消語彙基元。  
  
### <a name="return-value"></a>傳回值  
 一項工作會在所有輸入工作都順利完成時，順利完成。 如果輸入工作的類型為 `T`，則這個函式的輸出會是 `task<std::pair<T, size_t>>>`，其中配對的第一個項目是完成工作的結果，而第二個項目是已完成工作的索引。 如果輸入工作的類型為 `void`，則輸出是 `task<size_t>`，其中結果是完成工作的索引。  
  
### <a name="remarks"></a>備註  
 `when_any` 是未封鎖的函式，會產生 `task` 做為其結果。 不同於[task:: wait](task-class.md#wait)，您可以放心在 ASTA (應用程式 STA) 執行緒上的 UWP 應用程式呼叫此函式。  
  
 如需詳細資訊，請參閱[工作平行處理原則](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)
