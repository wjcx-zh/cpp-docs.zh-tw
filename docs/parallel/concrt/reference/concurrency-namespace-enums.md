---
title: concurrency 命名空間列舉
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 8b9aec0a3464b921ca80f731ac4a3c26e72ef34e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832239"
---
# <a name="concurrency-namespace-enums"></a>concurrency 命名空間列舉

:::row:::
   :::column span="":::
      [`agent_status`](#agent_status)\
      [`Agents_EventType`](#agents_eventtype)\
      [`ConcRT_EventType`](#concrt_eventtype)\
      [`Concrt_TraceFlags`](#concrt_traceflags)\
      [`CriticalRegionType`](#criticalregiontype)
   :::column-end:::
   :::column span="":::
      [`DynamicProgressFeedbackType`](#dynamicprogressfeedbacktype)\
      [`join_type`](#join_type)\
      [`message_status`](#message_status)\
      [`PolicyElementKey`](#policyelementkey)\
      [`SchedulerType`](#schedulertype)
   :::column-end:::
   :::column span="":::
      [`SchedulingProtocolType`](#schedulingprotocoltype)\
      [`SwitchingProxyState`](#switchingproxystate)\
      [`task_group_status`](#task_group_status)\
      [`WinRTInitializationType`](#winrtinitializationtype)
   :::column-end:::
:::row-end:::

## <a name="agent_status-enumeration"></a><a name="agent_status"></a> agent_status 列舉

`agent` 的有效狀態。

```cpp
enum agent_status;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`agent_canceled`|已取消 `agent`。|
|`agent_created`|`agent`已建立但未啟動。|
|`agent_done`|`agent`完成但不取消。|
|`agent_runnable`|已 `agent` 啟動，但未輸入其 `run` 方法。|
|`agent_started`|`agent`已啟動。|

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [非同步代理](../../../parallel/concrt/asynchronous-agents.md)程式。

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a> Agents_EventType 列舉

可以使用代理程式程式庫所提供之追蹤功能追蹤的事件類型

```cpp
enum Agents_EventType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|表示建立物件的事件類型|
|`AGENTS_EVENT_DESTROY`|表示刪除物件的事件類型|
|`AGENTS_EVENT_END`|表示某些處理完成的事件類型|
|`AGENTS_EVENT_LINK`|表示連結訊息區的事件類型|
|`AGENTS_EVENT_NAME`|表示物件名稱的事件類型|
|`AGENTS_EVENT_SCHEDULE`|表示排程處理序的事件類型|
|`AGENTS_EVENT_START`|表示啟始某項處理的事件類型|
|`AGENTS_EVENT_UNLINK`|表示取消連結訊息區的事件類型|

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a> ConcRT_EventType 列舉

可以使用並行執行階段所提供的追蹤功能追蹤的事件類型。

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|表示附加至排程器之動作的事件種類。|
|`CONCRT_EVENT_BLOCK`|表示內容封鎖之動作的事件種類。|
|`CONCRT_EVENT_DETACH`|表示從排程器卸離之動作的事件種類。|
|`CONCRT_EVENT_END`|標示開始/結束事件配對開頭的事件種類。|
|`CONCRT_EVENT_GENERIC`|用於其他事件的事件種類。|
|`CONCRT_EVENT_IDLE`|表示內容變成閒置之動作的事件種類。|
|`CONCRT_EVENT_START`|標示開始/結束事件配對開頭的事件種類。|
|`CONCRT_EVENT_UNBLOCK`|表示解除封鎖內容之動作的事件種類。|
|`CONCRT_EVENT_YIELD`|表示內容產生之動作的事件種類。|

### <a name="requirements"></a>規格需求

**Header：** Concrt .H **命名空間：** concurrency

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a> Concrt_TraceFlags 列舉

事件類型的追蹤旗標。

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a> CriticalRegionType 列舉

內含內容之關鍵區域的類型。

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`InsideCriticalRegion`|指出內容在重要區域內。 當在重要區域內時，會從排程器中隱藏非同步暫停。 如果發生這種情況，Resource Manager 會等待中的執行緒變成可執行，並直接繼續執行，而不是重新叫用排程器。 在這類區域內所採取的任何鎖定都必須非常小心。|
|`InsideHyperCriticalRegion`|指出內容在超關鍵區域內。 當在超關鍵區域內時，同步和非同步暫停會在排程器中隱藏。 如果發生這種暫停或封鎖，resource manager 會等待中的執行緒變成可執行，並直接繼續執行，而不是重新叫用排程器。 在這類區域內進行的鎖定絕對不可與在這類區域以外執行的程式碼共用。 這麼做會導致無法預期的鎖死。|
|`OutsideCriticalRegion`|指出內容在任何重要區域之外。|

### <a name="requirements"></a>規格需求

**標頭：** concrtrm。h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a> DynamicProgressFeedbackType 列舉

`DynamicProgressFeedback` 原則用來描述要根據從排程器收集到的統計資訊重新平衡排程器的資源，或者只要根據透過 `IVirtualProcessorRoot` 介面上的 `Activate` 和 `Deactivate` 方法呼叫進出閒置狀態的虛擬處理器。 如需可用排程器原則的詳細資訊，請參閱 [PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ProgressFeedbackDisabled`|排程器不會收集進度資訊。 重新平衡只會根據基礎硬體執行緒的訂用帳戶層級進行。 如需訂用帳戶層級的詳細資訊，請參閱 [IExecutionResource：： CurrentSubscriptionLevel](IExecutionResource-structure.md)。<br /><br /> 這個值已保留供執行時間使用。|
|`ProgressFeedbackEnabled`|排程器會收集進度資訊，並將其傳遞給資源管理員。 除了基礎硬體執行緒的訂用帳戶層級以外，resource manager 將利用此統計資訊來代表排程器重新平衡資源。 如需訂用帳戶層級的詳細資訊，請參閱 [IExecutionResource：： CurrentSubscriptionLevel](IExecutionResource-structure.md)。|

## <a name="join_type-enumeration"></a><a name="join_type"></a> join_type 列舉

`join` 傳訊區塊的類型。

```cpp
enum join_type;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`greedy`|貪婪 `join` 訊息區塊會立即在傳播時接受訊息。 這會更有效率，但根據網路設定，有可能進行即時鎖定。|
|`non_greedy`|非貪婪的 `join` 訊息區塊會延後訊息，並在所有訊息抵達後嘗試並使用。 這些保證可以運作，但速度較慢。|

### <a name="requirements"></a>規格需求

**標頭：** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a> message_status 列舉

`message` 物件對區塊供應項目的有效回應。

```cpp
enum message_status;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`accepted`|目標已接受訊息。|
|`declined`|目標未接受訊息。|
|`missed`|目標嘗試接受訊息，但無法再使用。|
|`postponed`|已延後訊息的目標。|

### <a name="requirements"></a>規格需求

**標頭：** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a> PolicyElementKey 列舉

描述排程器行為方面的原則機碼。 每個原則項目由一個機碼值組描述。 如需排程器原則及其對排程器之影響的詳細資訊，請參閱 [工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ContextPriority`|排程器中每個內容的作業系統執行緒優先順序。 如果此索引鍵設定為值，則排程器中的內容 `INHERIT_THREAD_PRIORITY` 將會繼承建立排程器之執行緒的優先順序。<br /><br /> 有效值： Windows 函數的任何有效值 `SetThreadPriority` 和特殊值 `INHERIT_THREAD_PRIORITY`<br /><br /> 預設值： `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|排程器中每個內容的保留堆疊大小（以 kb 為單位）。<br /><br /> 有效的值：正整數<br /><br /> 預設值： `0` ，表示使用處理程式的堆疊大小預設值。|
|`DynamicProgressFeedback`|決定是否要根據從排程器收集的統計資訊，或僅根據基礎硬體執行緒的訂用帳戶層級，來重新平衡排程器的資源。 如需詳細資訊，請參閱 [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)。<br /><br /> 有效的值：列舉的成員 `DynamicProgressFeedbackType` ， `ProgressFeedbackEnabled` 也就是或 `ProgressFeedbackDisabled`<br /><br /> 預設值： `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|當 `SchedulingProtocol` 原則金鑰設定為值時 `EnhanceScheduleGroupLocality` ，這個值會指定每個虛擬處理器本機佇列中允許快取的可執行內容數目上限。 這類內容通常會以後進先出的 (LIFO) 順序在導致它們可執行檔虛擬處理器上執行。 請注意，當 `SchedulingProtocol` 金鑰設定為值時，此原則金鑰沒有任何意義 `EnhanceForwardProgress` 。<br /><br /> 有效的值：非負整數<br /><br /> 預設值： `8`|
|`MaxConcurrency`|排程器所需的最大並行層級。 資源管理員會嘗試一開始配置這多個虛擬處理器。 特殊值 [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) 表示所需的並行層級與電腦上的硬體執行緒數目相同。 如果指定的值 `MinConcurrency` 大於電腦上的硬體執行緒數目，且 `MaxConcurrency` 指定為 `MaxExecutionResources` ，則會引發的值 `MaxConcurrency` 以符合所設定的值 `MinConcurrency` 。<br /><br /> 有效的值：正整數和特殊值 `MaxExecutionResources`<br /><br /> 預設值： `MaxExecutionResources`|
|`MaxPolicyElementKey`|最大原則元素索引鍵。 不是有效的元素索引鍵。|
|`MinConcurrency`|資源管理員必須提供給排程器的最小平行存取層級。 指派給排程器的虛擬處理器數目絕不會低於最小值。 特殊值 [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) 表示最小並行層級與電腦上的硬體執行緒數目相同。 如果指定的值 `MaxConcurrency` 小於電腦上的硬體執行緒數目，且 `MinConcurrency` 指定為 `MaxExecutionResources` ，的值 `MinConcurrency` 會降低，以符合所設定的值 `MaxConcurrency` 。<br /><br /> 有效的值：非負整數和特殊值 `MaxExecutionResources` 。 請注意，對於用於建構並行執行階段排程器的排程器原則，`0` 值無效。<br /><br /> 預設值： `1`|
|`SchedulerKind`|排程器將針對基礎執行內容使用的執行緒類型。 如需詳細資訊，請參閱 [SchedulerType](#schedulertype)。<br /><br /> 有效值：`SchedulerType` 列舉的成員，例如 `ThreadScheduler`。<br /><br /> 預設值： `ThreadScheduler` 。 這會轉譯為所有作業系統上的 Win32 執行緒。|
|`SchedulingProtocol`|描述排程器將使用的排程演算法。 如需詳細資訊，請參閱 [SchedulingProtocolType](#schedulingprotocoltype)。<br /><br /> 有效的值：列舉的成員 `SchedulingProtocolType` ， `EnhanceScheduleGroupLocality` 也就是或 `EnhanceForwardProgress`<br /><br /> 預設值： `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|每個硬體執行緒的暫時性虛擬處理器數目。 如有必要，資源管理員可以增加目標過度訂閱因數，以滿足電腦上硬體執行緒的 `MaxConcurrency`。<br /><br /> 有效的值：正整數<br /><br /> 預設值： `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a> SchedulerType 列舉

`SchedulerKind` 原則用來描述排程器應用於基礎執行內容的執行緒類型。 如需可用排程器原則的詳細資訊，請參閱 [PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum SchedulerType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ThreadScheduler`|指出一般 Win32 執行緒的明確要求。|
|`UmsThreadDefault`|Visual Studio 2013 中的並行執行階段不支援使用者模式可排程 (UMS) 執行緒。 使用 `UmsThreadDefault` 做為 `SchedulerType` 原則的值不會產生錯誤。 然而，以這個原則建立的排程器將會預設為使用 Win32 執行緒。|

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a> SchedulingProtocolType 列舉

`SchedulingProtocol` 原則用於描述排程器將使用的排程演算法。 如需可用排程器原則的詳細資訊，請參閱 [PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`EnhanceForwardProgress`|排程器會在執行每個工作之後，優先透過排程群組來迴圈配置資源。 已解除封鎖的內容通常是以先進先出的 (FIFO) 方式來排程。 虛擬處理器不會快取解除封鎖的內容。|
|`EnhanceScheduleGroupLocality`|排程器偏好在移至另一個排程群組之前，繼續處理目前排程群組內的工作。 已解除封鎖的內容會針對每個虛擬處理器進行快取，而且通常會以後進先出的 (LIFO) 方式，以將其解除封鎖的虛擬處理器進行排程。|

### <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a> SwitchingProxyState 列舉

用來表示執行緒 Proxy 所處的狀態 (當它正在執行將合作內容切換到不同的執行緒 Proxy 時)。

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`Blocking`|指出呼叫端執行緒會以合作方式封鎖，而且應該是由呼叫端獨佔擁有，直到後續再次執行並執行其他動作為止。|
|`Idle`|指出排程器不再需要呼叫的執行緒，而且會傳回 Resource Manager。 Resource Manager 無法再利用已分派的內容。|
|`Nesting`|指出呼叫端執行緒會嵌套子排程器，而且呼叫端需要這些執行緒才能附加至不同的排程器。|

### <a name="remarks"></a>備註

型別的參數 `SwitchingProxyState` 會傳遞至方法 `IThreadProxy::SwitchTo` ，以指示 Resource Manager 如何處理髮出呼叫的執行緒 proxy。

如需如何使用此類型的詳細資訊，請參閱 [IThreadProxy：： SwitchTo](ithreadproxy-structure.md#switchto)。

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a> task_group_status 列舉

描述 `task_group` 或 `structured_task_group` 物件的執行狀態。 等待預定工作群組完成工作的許多方法，會傳回這個類型的值。

```cpp
enum task_group_status;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`canceled`|`task_group` 或 `structured_task_group` 物件已取消。 可能有一個或多個工作尚未執行。|
|`completed`|在 `task_group` 或 `structured_task_group` 物件列隊的工作已順利完成。|
|`not_complete`|在 `task_group` 物件列隊的工作尚未完成。 請注意，目前不會由並行執行階段傳回這個值。|

### <a name="requirements"></a>規格需求

**標頭：** pplinterface。h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a> WinRTInitializationType 列舉

由 `WinRTInitialization` 原則用來描述 Windows 執行階段是否會在執行 Windows 8 (含) 以後版本作業系統之應用程式的排程器執行緒上初始化，以及如何進行初始化。 如需可用排程器原則的詳細資訊，請參閱 [PolicyElementKey](concurrency-namespace-enums.md)。

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`DoNotInitializeWinRT`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，則排程器內的執行緒將不會初始化 Windows 執行階段。|
|`InitializeWinRTAsMTA`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，排程器內的每個執行緒將會初始化 Windows 執行階段，並將它宣告為多執行緒 Apartment 的一部分。|

## <a name="requirements"></a>規格需求

**標頭：** concrt。h

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
