---
title: concurrency 命名空間列舉 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69b11a78d1be76895b9687d1423df74c51fe3d39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416691"
---
# <a name="concurrency-namespace-enums"></a>concurrency 命名空間列舉

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

##  <a name="agent_status"></a>  agent_status 列舉

`agent` 的有效狀態。

```
enum agent_status;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`agent_canceled`|已取消 `agent`。|
|`agent_created`|`agent`已建立但未啟動。|
|`agent_done`|`agent`完成，沒有被取消。|
|`agent_runnable`|`agent`已啟動，但未輸入其`run`方法。|
|`agent_started`|`agent`已啟動。|

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0> [ 非同步代理程式](../../../parallel/concrt/asynchronous-agents.md)。

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="agents_eventtype"></a>  Agents_EventType 列舉

可以使用代理程式程式庫所提供之追蹤功能追蹤的事件類型

```
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

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="concrt_eventtype"></a>  ConcRT_EventType Enumeration

可以使用並行執行階段所提供的追蹤功能追蹤的事件類型。

```
enum ConcRT_EventType;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|事件類型，表示附加至排程器的動作。|
|`CONCRT_EVENT_BLOCK`|表示的內容，封鎖動作的事件類型。|
|`CONCRT_EVENT_DETACH`|事件類型，代表從排程器中斷連線的動作。|
|`CONCRT_EVENT_END`|標示起點開始/結束事件配對的事件類型。|
|`CONCRT_EVENT_GENERIC`|用於其他事件的事件類型。|
|`CONCRT_EVENT_IDLE`|表示進入閒置狀態的內容中的動作的事件類型。|
|`CONCRT_EVENT_START`|標示起點開始/結束事件配對的事件類型。|
|`CONCRT_EVENT_UNBLOCK`|事件類型，代表解除封鎖的內容中的動作。|
|`CONCRT_EVENT_YIELD`|表示的內容，產生動作的事件類型。|

### <a name="requirements"></a>需求

**標頭：** concrt.h**命名空間：** 並行存取

##  <a name="concrt_traceflags"></a>  Concrt_TraceFlags 列舉

事件類型的追蹤旗標。

```
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

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="criticalregiontype"></a>  CriticalRegionType 列舉

內含內容之關鍵區域的類型。

```
enum CriticalRegionType;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`InsideCriticalRegion`|指出內容是在關鍵區域內。 在關鍵區域內非同步的暫止會隱藏來自排程器。 應暫止發生，Resource Manager 將會等候執行緒變成可執行，並只需繼續它而不是再次叫用的排程器。 極審慎地，必須採取這種區域內任何鎖定。|
|`InsideHyperCriticalRegion`|指出內容位於超關鍵區域。 在超關鍵區域內同步和非同步的暫止會隱藏來自排程器。 應暫止或封鎖發生，資源管理員會等候執行緒變成可執行，並只需繼續它而不是再次叫用的排程器。 在這種區域內的鎖定必須永遠不會共用這類區域外部的執行程式碼。 如此一來，將會導致無法預期的死結。|
|`OutsideCriticalRegion`|指出內容超出任何關鍵區域。|

### <a name="requirements"></a>需求

**標頭：** concrtrm.h

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType Enumeration

`DynamicProgressFeedback` 原則用來描述要根據從排程器收集到的統計資訊重新平衡排程器的資源，或者只要根據透過 `IVirtualProcessorRoot` 介面上的 `Activate` 和 `Deactivate` 方法呼叫進出閒置狀態的虛擬處理器。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md)。

```
enum DynamicProgressFeedbackType;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ProgressFeedbackDisabled`|排程器不會收集進度資訊。 重新平衡是取決於基礎硬體執行緒的訂用帳戶層級。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](IExecutionResource-structure.md)。<br /><br /> 此值已保留供執行階段。|
|`ProgressFeedbackEnabled`|排程器會收集進度資訊，並將它傳遞給資源管理員。 資源管理員會利用這個重新平衡資源代表除了訂用帳戶層級的基礎硬體執行緒排程器的統計資訊。 如需有關訂用帳戶層級的詳細資訊，請參閱[iexecutionresource:: Currentsubscriptionlevel](IExecutionResource-structure.md)。|
##  <a name="join_type"></a>  join_type 列舉

`join` 傳訊區塊的類型。

```
enum join_type;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`greedy`|Greedy （窮盡)`join`傳訊區塊會立即接受訊息，以在傳播時。 這會更有效率，但有即時鎖定視網路組態而定的可能性時。|
|`non_greedy`|非窮盡`join`傳訊區塊延後訊息，並再試，並取用後所有已到達。 這些會保證可以運作，但速度變慢。|

### <a name="requirements"></a>需求

**標頭：** agents.h

##  <a name="message_status"></a>  message_status 列舉

`message` 物件對區塊供應項目的有效回應。

```
enum message_status;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`accepted`|目標已接受訊息。|
|`declined`|目標不接受訊息。|
|`missed`|目標嘗試接受訊息，但已無法使用。|
|`postponed`|目標延後訊息。|

### <a name="requirements"></a>需求

**標頭：** agents.h

##  <a name="policyelementkey"></a>  PolicyElementKey 列舉

描述排程器行為方面的原則機碼。 每個原則項目由一個機碼值組描述。 如需排程器排程器原則和其影響的相關詳細資訊，請參閱[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

```
enum PolicyElementKey;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ContextPriority`|排程器中的每個內容的作業系統執行緒優先權。 如果此機碼設定為值`INHERIT_THREAD_PRIORITY`排程器中的內容會繼承建立排程器執行緒的優先權。<br /><br /> 有效值： 任何有效的值，如 Windows`SetThreadPriority`函式和特殊值 `INHERIT_THREAD_PRIORITY`<br /><br /> 預設值： `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|在排程器，以 kb 為單位的每個內容保留的堆疊大小。<br /><br /> 有效值： 正整數<br /><br /> 預設值： `0`，表示使用的堆疊大小的處理序的預設值。|
|`DynamicProgressFeedback`|判斷是否會根據從排程器收集，或只根據基礎硬體執行緒的訂用帳戶層級的統計資訊重新平衡排程器的資源。 如需詳細資訊，請參閱 < [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)。<br /><br /> 有效值： 隸屬`DynamicProgressFeedbackType`列舉型別，可以是`ProgressFeedbackEnabled`或 `ProgressFeedbackDisabled`<br /><br /> 預設值： `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|當`SchedulingProtocol`原則機碼設定為值`EnhanceScheduleGroupLocality`，這會指定可執行的內容快取中每個虛擬處理器的本機佇列的最大數目。 此類內容通常會以先進先出 (LIFO) 順序，使其變成可執行的虛擬處理器上執行。 請注意，此原則機碼的任何這表示當`SchedulingProtocol`機碼設定為值`EnhanceForwardProgress`。<br /><br /> 有效值： 是非負整數<br /><br /> 預設值： `8`|
|`MaxConcurrency`|排程器層級所需的最大並行存取。 資源管理員會試著一開始配置這麼多的虛擬處理器。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)指出所需的並行層級是相同的電腦上的硬體執行緒數目。 如果指定的值`MinConcurrency`的電腦上的硬體執行緒數目大於並`MaxConcurrency`指定為`MaxExecutionResources`的值`MaxConcurrency`符合的設定為何，會引發`MinConcurrency`。<br /><br /> 有效值： 正整數和特殊值 `MaxExecutionResources`<br /><br /> 預設值： `MaxExecutionResources`|
|`MaxPolicyElementKey`|最大的原則項目索引鍵。 不是有效的項目索引鍵。|
|`MinConcurrency`|必須由資源管理員的 排程器提供的最小的並行處理等級。 指派給排程器的虛擬處理器數目，永遠不會低於最小值。 特殊值[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)表示最小的並行層級是相同的電腦上的硬體執行緒數目。 如果指定的值`MaxConcurrency`的電腦上的硬體執行緒數目小於並`MinConcurrency`指定為`MaxExecutionResources`的值`MinConcurrency`降低到符合的設定為何`MaxConcurrency`。<br /><br /> 有效值： 非負整數和特殊值`MaxExecutionResources`。 請注意，對於用於建構並行執行階段排程器的排程器原則，`0` 值無效。<br /><br /> 預設值： `1`|
|`SchedulerKind`|排程器將會利用之基礎執行內容的執行緒類型。 如需詳細資訊，請參閱 < [SchedulerType](#schedulertype)。<br /><br /> 有效值：`SchedulerType` 列舉的成員，例如 `ThreadScheduler`。<br /><br /> 預設值： `ThreadScheduler`。 這會轉譯為在所有作業系統上的 Win32 執行緒。|
|`SchedulingProtocol`|描述排程演算法會使用排程器。 如需詳細資訊，請參閱 < [SchedulingProtocolType](#schedulingprotocoltype)。<br /><br /> 有效值： 隸屬`SchedulingProtocolType`列舉型別，可以是`EnhanceScheduleGroupLocality`或 `EnhanceForwardProgress`<br /><br /> 預設值： `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|暫時性的每個硬體執行緒的虛擬處理器數目。 如有必要，資源管理員可以增加目標過度訂閱因數，以滿足電腦上硬體執行緒的 `MaxConcurrency`。<br /><br /> 有效值： 正整數<br /><br /> 預設值： `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="schedulertype"></a>  SchedulerType 列舉

`SchedulerKind` 原則用來描述排程器應用於基礎執行內容的執行緒類型。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md)。

```
enum SchedulerType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ThreadScheduler`|表示明確要求的一般 Win32 執行緒。|
|`UmsThreadDefault`|在 Visual Studio 2013 並行執行階段不支援使用者模式排程 (UMS) 執行緒。 使用 `UmsThreadDefault` 做為 `SchedulerType` 原則的值不會產生錯誤。 然而，以這個原則建立的排程器將會預設為使用 Win32 執行緒。|

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="schedulingprotocoltype"></a>  SchedulingProtocolType 列舉

`SchedulingProtocol` 原則用於描述排程器將使用的排程演算法。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md)。

```
enum SchedulingProtocolType;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`EnhanceForwardProgress`|排程器偏好透過排程群組的循環之後執行每項工作。 解除封鎖的內容通常會排定後進先出 (FIFO) 的方式。 虛擬處理器不會快取解除封鎖的內容。|
|`EnhanceScheduleGroupLocality`|排程器偏好繼續移至另一個排程群組之前處理目前的排程群組內的工作。 解除封鎖的內容會快取每個虛擬處理器，而且通常後進先出 (LIFO) 的方式排程虛擬處理器的解除封鎖它們。|

### <a name="requirements"></a>需求

**標頭：** concrt.h

##  <a name="switchingproxystate"></a>  SwitchingProxyState 列舉

用來表示執行緒 Proxy 所處的狀態 (當它正在執行將合作內容切換到不同的執行緒 Proxy 時)。

```
enum SwitchingProxyState;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`Blocking`|表示以合作方式封鎖呼叫執行緒，而且必須獨佔擁有由呼叫端直到之後再次執行，而且執行其他動作。|
|`Idle`|指出呼叫執行緒不再需要排程器，以及傳回至 Resource Manager。 已發送的內容已不再能夠使用資源管理員。|
|`Nesting`|指出呼叫的執行緒巢狀的子系排程器，並藉由呼叫者，才能附加至不同的排程器。|

### <a name="remarks"></a>備註

類型的參數`SwitchingProxyState`會傳遞至方法中`IThreadProxy::SwitchTo`指示資源管理員如何處理正在進行呼叫的執行緒 proxy。

如需有關如何使用這種類型的詳細資訊，請參閱 < [ithreadproxy:: Switchto](ithreadproxy-structure.md#switchto)。

##  <a name="task_group_status"></a>  task_group_status 列舉

描述 `task_group` 或 `structured_task_group` 物件的執行狀態。 等待預定工作群組完成工作的許多方法，會傳回這個類型的值。

```
enum task_group_status;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`canceled`|`task_group` 或 `structured_task_group` 物件已取消。 可能有一個或多個工作尚未執行。|
|`completed`|在 `task_group` 或 `structured_task_group` 物件列隊的工作已順利完成。|
|`not_complete`|在 `task_group` 物件列隊的工作尚未完成。 請注意，目前不會由並行執行階段傳回這個值。|

### <a name="requirements"></a>需求

**標頭：** pplinterface.h

##  <a name="winrtinitializationtype"></a>  WinRTInitializationType 列舉

由 `WinRTInitialization` 原則用來描述 Windows 執行階段是否會在執行 Windows 8 (含) 以後版本作業系統之應用程式的排程器執行緒上初始化，以及如何進行初始化。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md)。

```
enum WinRTInitializationType;
```
### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`DoNotInitializeWinRT`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，則排程器內的執行緒將不會初始化 Windows 執行階段。|
|`InitializeWinRTAsMTA`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，排程器內的每個執行緒將會初始化 Windows 執行階段，並將它宣告為多執行緒 Apartment 的一部分。|

## <a name="requirements"></a>需求

**標頭：** concrt.h

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
