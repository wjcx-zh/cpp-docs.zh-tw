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
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372716"
---
# <a name="concurrency-namespace-enums"></a>concurrency 命名空間列舉

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[臨界區域類型](#criticalregiontype)|[動態進度回饋](#dynamicprogressfeedbacktype)|[策略元素鍵](#policyelementkey)|
|[排程類型](#schedulertype)|[排程協定類型](#schedulingprotocoltype)|[切換代理狀態](#switchingproxystate)|
|[WinRT 初始化類型](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status枚舉

`agent` 的有效狀態。

```cpp
enum agent_status;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`agent_canceled`|已取消 `agent`。|
|`agent_created`|`agent`已創建但未啟動。|
|`agent_done`|完成`agent`而不被取消。|
|`agent_runnable`|`agent`已啟動,但未輸入其`run`方法。|
|`agent_started`|已`agent`啟動。|

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[非同步代理](../../../parallel/concrt/asynchronous-agents.md)。

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType枚舉

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

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType枚舉

可以使用並行執行階段所提供的追蹤功能追蹤的事件類型。

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|表示附加到計畫程式的行為的事件類型。|
|`CONCRT_EVENT_BLOCK`|表示上下文阻止行為的事件類型。|
|`CONCRT_EVENT_DETACH`|表示從計劃程式分離的行為的事件類型。|
|`CONCRT_EVENT_END`|標記開始/結束事件對開頭的事件類型。|
|`CONCRT_EVENT_GENERIC`|用於雜項事件的事件類型。|
|`CONCRT_EVENT_IDLE`|表示上下文變為空閒行為的事件類型。|
|`CONCRT_EVENT_START`|標記開始/結束事件對開頭的事件類型。|
|`CONCRT_EVENT_UNBLOCK`|表示取消阻止上下文的行為的事件類型。|
|`CONCRT_EVENT_YIELD`|表示上下文產生行為的事件類型。|

### <a name="requirements"></a>需求

**標題:** concrt.h**命名空間:** 併發性

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags枚舉

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

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>臨界區域類型枚舉

內含內容之關鍵區域的類型。

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`InsideCriticalRegion`|指示上下文位於關鍵區域內。 在關鍵區域內時,非同步掛起會隱藏在調度程式中。 如果發生此類掛起,資源管理器將等待線程變為可運行線程,然後簡單地恢復該線程,而不是再次調用計劃程式。 必須極其小心地在此類區域內取下任何鎖。|
|`InsideHyperCriticalRegion`|指示上下文位於超臨界區域內。 在超臨界區域內時,同步和非同步掛起都會從計畫程式隱藏。 如果發生此類掛起或阻塞,資源管理器將等待線程變為可運行線程,然後簡單地恢復該線程,而不是再次調用計劃程式。 在此類區域內獲取的鎖絕不能與在此類區域之外運行的代碼共用。 這樣做將導致不可預知的僵局。|
|`OutsideCriticalRegion`|指示上下文在任何關鍵區域之外。|

### <a name="requirements"></a>需求

**標題:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>動態進度回饋型態

`DynamicProgressFeedback` 原則用來描述要根據從排程器收集到的統計資訊重新平衡排程器的資源，或者只要根據透過 `IVirtualProcessorRoot` 介面上的 `Activate` 和 `Deactivate` 方法呼叫進出閒置狀態的虛擬處理器。 有關可用計畫程式政策的詳細資訊,請參考[策略元素鍵](concurrency-namespace-enums.md)。

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ProgressFeedbackDisabled`|計劃程式不收集進度資訊。 重新平衡僅基於基礎硬體線程的訂閱級別完成。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](IExecutionResource-structure.md)。<br /><br /> 此值保留供運行時使用。|
|`ProgressFeedbackEnabled`|計劃程式收集進度資訊並將其傳遞給資源管理器。 資源管理器將使用此統計資訊代表計劃程式重新平衡資源,以及基礎硬體線程的訂閱級別。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](IExecutionResource-structure.md)。|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type枚舉

`join` 傳訊區塊的類型。

```cpp
enum join_type;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`greedy`|貪`join`婪的消息塊在傳播時立即接受消息。 這更有效,但可以進行即時鎖定,具體取決於網路配置。|
|`non_greedy`|非貪婪`join`的消息塊推遲消息,並嘗試使用它們后,所有到達。 這些保證工作,但速度較慢。|

### <a name="requirements"></a>需求

**標頭：** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status枚舉

`message` 物件對區塊供應項目的有效回應。

```cpp
enum message_status;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`accepted`|目標接受消息。|
|`declined`|目標不接受該消息。|
|`missed`|目標嘗試接受該消息,但它不再可用。|
|`postponed`|目標推遲了消息。|

### <a name="requirements"></a>需求

**標頭：** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>策略元素鍵列舉

描述排程器行為方面的原則機碼。 每個原則項目由一個機碼值組描述。 有關計劃程式原則及其對計畫程式的影響的詳細資訊,請參閱[工作計畫程式](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ContextPriority`|計劃程式中每個上下文的操作系統線程優先順序。 如果此鍵設置為值`INHERIT_THREAD_PRIORITY`,則計劃程式中的上下文將繼承創建計劃程式的線程的優先順序。<br /><br /> 有效值 :Windows`SetThreadPriority`函數的任何有效值和特殊值`INHERIT_THREAD_PRIORITY`<br /><br /> 預設值 :`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|計劃程式中每個上下文的保留堆疊大小(以千位元組為單位)。<br /><br /> 有效值 :正整數<br /><br /> 預設值 :,`0`指示使用行程堆疊大小的預設值。|
|`DynamicProgressFeedback`|確定計劃程式的資源是根據從計劃程式收集的統計資訊重新平衡,還是僅根據基礎硬體線程的訂閱級別進行重新平衡。 有關詳細資訊,請參閱[動態進度回饋類型](#dynamicprogressfeedbacktype)。<br /><br /> 有效值`DynamicProgressFeedbackType`: enum 的`ProgressFeedbackEnabled`成員或`ProgressFeedbackDisabled`<br /><br /> 預設值 :`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|當`SchedulingProtocol`策略鍵設置為`EnhanceScheduleGroupLocality`值 時,這將指定允許每個虛擬處理器本地佇列中緩存的最大可運行上下文數。 此類上下文通常會在虛擬處理器上按最後一流 (LIFO) 順序運行,從而使它們變得可運行。 請注意,當鍵設置為值`SchedulingProtocol``EnhanceForwardProgress`時,此策略鍵沒有意義。<br /><br /> 有效值 :非負整數<br /><br /> 預設值 :`8`|
|`MaxConcurrency`|計劃程式所需的最大併發級別。 資源管理員將嘗試最初分配此許多虛擬處理器。 特殊值[Max 執行資源](concurrency-namespace-constants1.md#maxexecutionresources)指示所需的併發級別與電腦上的硬體線程數相同。 如果 指定`MinConcurrency``MaxConcurrency`的 值大於電腦上的硬體線程數,並且`MaxExecutionResources`指定`MaxConcurrency`為 , 則引發的`MinConcurrency`值以匹配 為設置的值。<br /><br /> 有效值 :正整數和特殊值`MaxExecutionResources`<br /><br /> 預設值 :`MaxExecutionResources`|
|`MaxPolicyElementKey`|最大策略元素鍵。 不是有效的元素鍵。|
|`MinConcurrency`|資源管理員必須提供給計劃程式的最小併發級別。 分配給計畫程式的虛擬處理器數永遠不會低於最小值。 特殊值[Max 執行資源](concurrency-namespace-constants1.md#maxexecutionresources)指示最小併發級別與計算機上的硬體線程數相同。 如果 為`MaxConcurrency``MinConcurrency`其 指定的值小於計算機上的硬體線程數,並且`MaxExecutionResources`指定為, 則將`MinConcurrency`降低的值`MaxConcurrency`以匹配為設置的值。<br /><br /> 合法值:非負整數和特殊值`MaxExecutionResources`。 請注意，對於用於建構並行執行階段排程器的排程器原則，`0` 值無效。<br /><br /> 預設值 :`1`|
|`SchedulerKind`|計劃程式將用於基礎執行上下文的線程類型。 有關詳細資訊,請參閱[計畫類型](#schedulertype)。<br /><br /> 有效值：`SchedulerType` 列舉的成員，例如 `ThreadScheduler`。<br /><br /> 預設值`ThreadScheduler`: . . 這轉換為所有作業系統上的 Win32 線程。|
|`SchedulingProtocol`|描述計畫程式將使用的調度演演演算法。 有關詳細資訊,請參閱[計畫協定類型](#schedulingprotocoltype)。<br /><br /> 有效值`SchedulingProtocolType`: enum 的`EnhanceScheduleGroupLocality`成員或`EnhanceForwardProgress`<br /><br /> 預設值 :`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|每個硬體線程的虛擬處理器的暫定數量。 如有必要，資源管理員可以增加目標過度訂閱因數，以滿足電腦上硬體執行緒的 `MaxConcurrency`。<br /><br /> 有效值 :正整數<br /><br /> 預設值 :`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>排程類型的枚舉

`SchedulerKind` 原則用來描述排程器應用於基礎執行內容的執行緒類型。 有關可用計畫程式政策的詳細資訊,請參考[策略元素鍵](concurrency-namespace-enums.md)。

```cpp
enum SchedulerType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`ThreadScheduler`|指示常規 Win32 線程的顯式請求。|
|`UmsThreadDefault`|在 Visual Studio 2013 中的併發運行時中不支援使用者模式可分劃 (UMS) 執行緒。 使用 `UmsThreadDefault` 做為 `SchedulerType` 原則的值不會產生錯誤。 然而，以這個原則建立的排程器將會預設為使用 Win32 執行緒。|

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>排程協定類型列舉

`SchedulingProtocol` 原則用於描述排程器將使用的排程演算法。 有關可用計畫程式政策的詳細資訊,請參考[策略元素鍵](concurrency-namespace-enums.md)。

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`EnhanceForwardProgress`|計劃程式更喜歡在執行每個任務後迴圈訪問計畫組。 未阻止的上下文通常以先出先出 (FIFO) 的方式安排。 虛擬處理器不會緩存未阻止的上下文。|
|`EnhanceScheduleGroupLocality`|計劃程式更喜歡在移動到另一個計劃組之前繼續處理當前計劃組中的任務。 未阻止的上下文按虛擬處理器緩存,通常由取消阻止它們的虛擬處理器以最後一先出 (LIFO) 的方式安排。|

### <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>切換代理狀態列舉

用來表示執行緒 Proxy 所處的狀態 (當它正在執行將合作內容切換到不同的執行緒 Proxy 時)。

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`Blocking`|指示調用線程是協同阻塞的,並且應由調用方獨佔,直到隨後再次運行並執行其他操作。|
|`Idle`|指示計劃程式不再需要調用線程,並且正在返回到資源管理器。 資源管理器不再能夠使用正在調度的上下文。|
|`Nesting`|指示調用線程嵌套子計劃程式,並且調用方需要調用線程,以便附加到其他計劃程式。|

### <a name="remarks"></a>備註

類型`SwitchingProxyState`參數傳入`IThreadProxy::SwitchTo`方法 ,以指示資源管理員如何處理進行呼叫的線程代理。

有關如何使用此類型的詳細資訊,請參閱[IThreadProxy::Switchto](ithreadproxy-structure.md#switchto)。

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status枚舉

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

### <a name="requirements"></a>需求

**標題:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>WinRT 初始化類型枚舉

由 `WinRTInitialization` 原則用來描述 Windows 執行階段是否會在執行 Windows 8 (含) 以後版本作業系統之應用程式的排程器執行緒上初始化，以及如何進行初始化。 有關可用計畫程式政策的詳細資訊,請參考[策略元素鍵](concurrency-namespace-enums.md)。

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`DoNotInitializeWinRT`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，則排程器內的執行緒將不會初始化 Windows 執行階段。|
|`InitializeWinRTAsMTA`|如果應用程式是在 Windows 8 (含) 以後版本的作業系統上執行，排程器內的每個執行緒將會初始化 Windows 執行階段，並將它宣告為多執行緒 Apartment 的一部分。|

## <a name="requirements"></a>需求

**標題:** concrt.h

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
