---
title: concurrency 命名空間
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: aa2fe7dedd1c7e1a8b5a72e01508b4201bd72a7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160066"
---
# <a name="concurrency-namespace"></a>concurrency 命名空間

`Concurrency` 命名空間提供可讓您存取並行執行階段 (C++ 的並行程式設計架構) 的類別和函式。 如需詳細資訊，請參閱[並行執行階段](../../../parallel/concrt/concurrency-runtime.md)。

## <a name="syntax"></a>語法

```
namespace concurrency;
```

## <a name="members"></a>成員

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|----------|-----------------|
|`runtime_object_identity`|每個訊息執行個體在傳訊元件之間受到複製和傳遞時，後面都會接一個識別。 該識別不可為訊息物件的位址。|
|`task_status`|代表工作終止狀態的類型。 有效值為 `completed` 和 `canceled`。|
|`TaskProc`|工作的基本抽象概念，定義為 `void (__cdecl * TaskProc)(void *)`。 會呼叫 `TaskProc` 來叫用工作的主體。|
|`TaskProc_t`|工作的基本抽象概念，定義為 `void (__cdecl * TaskProc_t)(void *)`。 會呼叫 `TaskProc` 來叫用工作的主體。|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[affinity_partitioner 類別](affinity-partitioner-class.md)|`affinity_partitioner` 類別與 `static_partitioner` 類別類似，不過，它可依據對應背景工作執行緒子範圍的選擇來改善快取依存性。 當迴圈重複執行相同的資料集，且快取容納得下該資料時，它可以大幅改善效能。 請注意，若要取得資料位置的優勢，必須使用相同的 `affinity_partitioner` 物件來搭配平行迴圈的後續反覆項目，且該平行迴圈應執行於特定資料集上。|
|[agent 類別](agent-class.md)|適合做為所有獨立代理程式之基底類別的類別。 它用來對其他代理程式隱藏狀態，並使用訊息傳遞互動。|
|[auto_partitioner 類別](auto-partitioner-class.md)|`auto_partitioner` 類別表示 `parallel_for`、`parallel_for_each` 和 `parallel_transform` 用來分割其逐一查看之範圍的預設方法。 這種分割方法會使用範圍竊取，來進行負載平衡及逐一查看取消作業。|
|[bad_target 類別](bad-target-class.md)|這個類別描述在傳訊區塊獲得目標的指標，但該目標對所執行的作業來說並不正確時，所擲回的例外狀況。|
|[call 類別](call-class.md)|`call` 傳訊區塊是一個多來源的排序 `target_block`，它在接收訊息時會叫用指定的函式。|
|[cancellation_token 類別](cancellation-token-class.md)|`cancellation_token` 類別表示可判斷某個作業是否已要求取消的能力。 特定語彙基元可以與 `task_group`、`structured_task_group` 或 `task` 產生關聯，來提供隱含取消作業。 如果與相關聯的 `cancellation_token_source` 已取消，也可以向它輪詢取消，或為它註冊回呼。|
|[cancellation_token_registration 類別](cancellation-token-registration-class.md)|`cancellation_token_registration` 類別表示來自 `cancellation_token` 的回呼通知。 當 `register` 的 `cancellation_token` 方法用來接收發生取消的通知時，則會傳回 `cancellation_token_registration` 物件做為回呼的控制代碼，讓呼叫端可以要求不再透過使用 `deregister` 方法發出的特定回呼。|
|[cancellation_token_source 類別](cancellation-token-source-class.md)|`cancellation_token_source` 類別代表取消某個可取消作業的能力。|
|[choice 類別](choice-class.md)|`choice` 傳訊區塊是多來源的單一目標區塊，代表與一組來源的控制流程互動。 選擇區塊會等候多個來源的其中一個來產生訊息，而且會傳播產生訊息之來源的索引。|
|[combinable 類別](combinable-class.md)|`combinable<T>` 物件適用於提供資料的執行緒私用複本，在平行演算法期間執行無鎖定的執行緒-本機子運算。 在平行作業結尾處，可以將執行緒私用子運算合併於最終結果。 這個類別可以用來代替共用變數，而且如果該共用變數有許多爭用情形，則可能可以改進效能。|
|[concurrent_priority_queue 類別](concurrent-priority-queue-class.md)|`concurrent_priority_queue` 類別允許多個執行緒同時推入和彈出項目。 項目會以優先權順序做為彈出依據，而優先權由函式提供的樣板引數決定。|
|[concurrent_queue 類別](concurrent-queue-class.md)|`concurrent_queue` 類別是一種序列容器類別，允許以先進先出的方式存取其項目。 它會啟用一組有限的並行安全作業，例如 `push` 和 `try_pop` 等。|
|[concurrent_unordered_map 類別](concurrent-unordered-map-class.md)|`concurrent_unordered_map` 類別是一種並行安全容器，可控制 `std::pair<const K, _Element_type>` 類型項目的不同長度序列。 序列的表示方式導致啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。|
|[concurrent_unordered_multimap 類別](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` 類別是一種並行安全容器，可控制 `std::pair<const K, _Element_type>` 類型項目的不同長度序列。 序列的表示方式導致啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。|
|[concurrent_unordered_multiset 類別](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset`類別是並行安全容器，可控制不同長度序列的項目型別 k。序列的表示方式啟用並行安全附加、 項目存取、 迭代器存取及迭代器周遊作業。|
|[concurrent_unordered_set 類別](concurrent-unordered-set-class.md)|`concurrent_unordered_set`類別是並行安全容器，可控制不同長度序列的項目型別 k。序列的表示方式啟用並行安全附加、 項目存取、 迭代器存取及迭代器周遊作業。|
|[concurrent_vector 類別](concurrent-vector-class.md)|`concurrent_vector` 類別是一種序列容器類別，允許以隨機方式存取任何項目。 它會啟用並行安全附加、項目存取、迭代器存取及迭代器周遊作業。|
|[Context 類別](context-class.md)|代表執行內容的抽象概念。|
|[context_self_unblock 類別](context-self-unblock-class.md)|這個類別描述從同樣的內容呼叫 `Context` 物件的 `Unblock` 方法所擲回的例外狀況。 這會指出指定內容自行解除封鎖的嘗試。|
|[context_unblock_unbalanced 類別](context-unblock-unbalanced-class.md)|這個類別描述時所擲回的例外狀況呼叫`Block`並`Unblock`方法`Context`物件未正確配對。|
|[critical_section 類別](critical-section-class.md)|其為並行執行階段明確察覺且不可重新進入的 Mutex。|
|[CurrentScheduler 類別](currentscheduler-class.md)|代表與呼叫內容相關之目前排程器的抽象概念。|
|[default_scheduler_exists 類別](default-scheduler-exists-class.md)|這個類別描述預設排程器已經存在於處理序中時呼叫 `Scheduler::SetDefaultSchedulerPolicy` 方法所擲回的例外狀況。|
|[event 類別](event-class.md)|其為並行執行階段明確察覺的手動重設事件。|
|[improper_lock 類別](improper-lock-class.md)|這個類別描述以不當的方式取得鎖定時擲回的例外狀況。|
|[improper_scheduler_attach 類別](improper-scheduler-attach-class.md)|這個類別描述當 `Scheduler` 物件已經附加到目前的內容上時呼叫 `Attach` 方法擲回的例外狀況。|
|[improper_scheduler_detach 類別](improper-scheduler-detach-class.md)|這個類別描述當尚未使用 `Scheduler` 物件的 `Attach` 方法將內容附加至任何排程器時呼叫 `CurrentScheduler::Detach` 方法所擲回的例外狀況。|
|[improper_scheduler_reference 類別](improper-scheduler-reference-class.md)|這個類別描述在被關閉的 `Scheduler` 物件 (來自不屬於排程器的內容) 上呼叫 `Reference` 方法所擲回的例外狀況。|
|[invalid_link_target 類別](invalid-link-target-class.md)|這個類別描述呼叫傳訊區塊的 `link_target` 方法，但傳訊區塊無法連結至目標時所擲回的例外狀況。 這是由於超過傳訊區塊允許連結數目或嘗試將特定目標連結至相同的來源兩次所導致。|
|[invalid_multiple_scheduling 類別](invalid-multiple-scheduling-class.md)|這個類別描述使用 `task_group` 或 `structured_task_group` 物件的 `run` 方法多次排程 `task_handle` 物件，而不中間變更呼叫 `wait` 或 `run_and_wait` 方法時擲回的例外狀況。|
|[invalid_operation 類別](invalid-operation-class.md)|這個類別描述執行無效的作業，且並行執行階段擲回的另一個例外狀況類型未正確描述該作業時，所擲回的例外狀況。|
|[invalid_oversubscribe_operation 類別](invalid-oversubscribe-operation-class.md)|這個類別描述將 `_BeginOversubscription` 參數設為 `false` 來呼叫 `Context::Oversubscribe` 方法，而不先將 `_BeginOversubscription` 參數設為 `true` 來呼叫 `Context::Oversubscribe` 方法時擲回的例外狀況。|
|[invalid_scheduler_policy_key 類別](invalid-scheduler-policy-key-class.md)|這個類別描述將無效或未知的機碼傳遞給 `SchedulerPolicy` 物件建構函式，或將必須使用其他方式 (如 `SetConcurrencyLimits` 方法) 變更的機碼傳遞給 `SchedulerPolicy` 物件的 `SetPolicyValue` 方法時所擲回的例外狀況。|
|[invalid_scheduler_policy_thread_specification 類別](invalid-scheduler-policy-thread-specification-class.md)|這個類別描述嘗試設定 `SchedulerPolicy` 物件的並行存取限制，以致 `MinConcurrency` 機碼的值小於 `MaxConcurrency` 機碼的值時擲回的例外狀況。|
|[invalid_scheduler_policy_value 類別](invalid-scheduler-policy-value-class.md)|這個類別描述在將 `SchedulerPolicy` 物件的原則機碼設為不正確的機碼值時擲回的例外狀況。|
|[ISource 類別](isource-class.md)|`ISource` 類別是所有來源區塊的介面。 來源區塊會將訊息傳播至 `ITarget` 區塊。|
|[ITarget 類別](itarget-class.md)|`ITarget` 類別是所有目標區塊的介面。 目標區塊會使用 `ISource` 區塊提供給它們的訊息。|
|[join 類別](join-class.md)|`join` 傳訊區塊是單一目標、多來源的排序 `propagator_block`，會與來自其每個來源的 `T` 類型訊息合併。|
|[location 類別](location-class.md)|硬體實體位置的抽象概念。|
|[message 類別](message-class.md)|基本訊息封套，其中包含在傳訊區塊之間傳遞的資料承載。|
|[message_not_found 類別](message-not-found-class.md)|這個類別描述在傳訊區塊找不到所要求之訊息時擲回的例外狀況。|
|[message_processor 類別](message-processor-class.md)|`message_processor` 類別是處理 `message` 物件的抽象基底類別。 訊息順序方面沒有一定的保證。|
|[missing_wait 類別](missing-wait-class.md)|這個類別描述 `task_group` 或 `structured_task_group` 物件的建構函式執行時卻仍有工作排程至該物件所擲回的例外狀況。 如果例外狀況導致堆疊回溯而達成解構函式，則永遠不會擲回此例外狀況。|
|[multi_link_registry 類別](multi-link-registry-class.md)|`multi_link_registry` 物件是管理多個來源區塊或多個目標區塊的 `network_link_registry`。|
|[multitype_join 類別](multitype-join-class.md)|`multitype_join` 傳訊區塊是多來源的單一目標傳訊區塊，會與來自其來源的不同類型訊息合併，並且為其目標提供 Tuple 合併的訊息。|
|[nested_scheduler_missing_detach 類別](nested-scheduler-missing-detach-class.md)|這個類別描述當並行執行階段偵測到您忘了使用 `Scheduler` 物件的 `Attach` 方法在附加到第二個排程器上呼叫 `CurrentScheduler::Detach` 方法時擲出的例外狀況。|
|[network_link_registry 類別](network-link-registry-class.md)|`network_link_registry` 抽象基底類別會管理來源和目標區塊之間的連結。|
|[operation_timed_out 類別](operation-timed-out-class.md)|這個類別描述作業逾時擲回的例外狀況。|
|[ordered_message_processor 類別](ordered-message-processor-class.md)|`ordered_message_processor` 是 `message_processor`，可讓訊息區塊按照接收順序處理訊息。|
|[overwrite_buffer 類別](overwrite-buffer-class.md)|`overwrite_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，一次能夠存放一個訊息。 新訊息會覆寫先前保留的訊息。|
|[progress_reporter 類別](progress-reporter-class.md)|進度報告程式類別可供報告特定類型的進度通知。 每個 progress_reporter 物件都會繫結至特定非同步動作或作業。|
|[propagator_block 類別](propagator-block-class.md)|`propagator_block` 類別是同時為來源和目標之訊息區塊的抽象基底類別。 它結合 `source_block` 和 `target_block` 類別的功能。|
|[reader_writer_lock 類別](reader-writer-lock-class.md)|以寫入器偏好設定佇列為基礎且只能本機微調的讀取器-寫入器鎖定。 鎖定會授與寫入器先進先出 (FIFO) 存取權，並在連續載入寫入器的情況下影響讀取器。|
|[ScheduleGroup 類別](schedulegroup-class.md)|代表排程群組的抽象概念。 排程群組會將一組相關的工作組織在一起，以讓這些工作獲得暫時緊密排程在一起的優勢，其方法如下：透過在同一個群組中執行另一個工作再移至另一個群組；透過再同一個 NUMA 節點或實體通訊端的同一個群組內執行多個項目。|
|[Scheduler 類別](scheduler-class.md)|代表並行執行階段排程器的抽象概念。|
|[scheduler_not_attached 類別](scheduler-not-attached-class.md)|這個類別描述作業需要將排程器附加至目前內容，而卻沒有這麼做時所擲回的例外狀況。|
|[scheduler_resource_allocation_error 類別](scheduler-resource-allocation-error-class.md)|這個類別描述因無法在並行執行階段中取得關鍵來源而擲回的例外狀況。|
|[scheduler_worker_creation_error 類別](scheduler-worker-creation-error-class.md)|這個類別描述因為無法建立並行執行階段中的背景工作執行內容而擲回的例外狀況。|
|[SchedulerPolicy 類別](schedulerpolicy-class.md)|`SchedulerPolicy` 類別包含一組索引鍵/值組，每個原則項目一個，可控制排程器執行個體的行為。|
|[simple_partitioner 類別](simple-partitioner-class.md)|`simple_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將這個範圍分割成區塊，每個區塊都有由區塊大小指定之反覆項目的最少次數。|
|[single_assignment 類別](single-assignment-class.md)|`single_assignment` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠儲存寫入一次的單一 `message`。|
|[single_link_registry 類別](single-link-registry-class.md)|`single_link_registry` 物件是只管理單一來源或目標區塊的 `network_link_registry`。|
|[source_block 類別](source-block-class.md)|`source_block` 類別是僅限來源區塊的抽象基底類別。 類別會提供基本連結管理功能與常見的錯誤檢查功能。|
|[source_link_manager 類別](source-link-manager-class.md)|`source_link_manager` 物件會管理 `ISource` 區塊與傳訊區塊網路的連結。|
|[static_partitioner 類別](static-partitioner-class.md)|`static_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將範圍分成許多區塊，其數量與基礎排程器可用的背景工作數量相等。|
|[structured_task_group 類別](structured-task-group-class.md)|`structured_task_group` 類別代表平行工作的高度結構化集合。 您可以使用 `task_handle` 物件，將個別平行工作佇列到 `structured_task_group` 中並等候這些工作完成，也可以在工作完成執行前取消工作群組，這樣會中止所有尚未開始執行的工作。|
|[target_block 類別](target-block-class.md)|`target_block` 類別是一種抽象基底類別，可提供基本的連結管理功能和僅限目標區塊的錯誤檢查。|
|[task 類別 (並行執行階段)](task-class.md)|平行模式程式庫 (PPL) `task` 類別。 `task` 物件代表可以非同步執行，並可與其他工作以及並行執行階段中平行演算法所產生的平行工作同時執行的工作。 成功完成時，會產生 `_ResultType` 類型的結果。 `task<void>` 類型的工作不會產生任何結果。 工作可以獨立於其他工作，個別等候及取消。 您也可以使用 continuations(`then`)、join(`when_all`) 和 choice(`when_any`) 等模式，將工作與其他工作組合在一起。|
|[task_canceled 類別](task-canceled-class.md)|這個類別描述 PPL 工作分層為了強制目前工作取消，而擲回的例外狀況。 它也會藉由擲回`get()`方法[工作](task-class.md)，已取消的工作。|
|[task_completion_event 類別](task-completion-event-class.md)|`task_completion_event` 類別可讓您延遲執行工作，直到滿足某條件，或是為了回應外部事件而開始工作。|
|[task_continuation_context 類別](task-continuation-context-class.md)|`task_continuation_context` 類別可讓您指定您想要執行接續的位置。 最好只從 UWP 應用程式使用此類別。 對於非 Windows 執行階段應用程式，工作接續的執行內容是由執行階段，而且不進行設定。|
|[task_group 類別](task-group-class.md)|`task_group` 類別表示可以等候或取消的平行工作集合。|
|[task_handle 類別](task-handle-class.md)|`task_handle` 類別代表個別的平行工作項目。 它會封裝執行工作所需的指示和資料。|
|[task_options 類別 (並行執行階段)](task-options-class-concurrency-runtime.md)|代表可用來建立工作的選項。|
|[timer 類別](timer-class.md)|`timer` 傳訊區塊是單一目標 `source_block`，能夠在經過指定的時間長度或在特定時間間隔，將訊息傳送至它的目標。|
|[transformer 類別](transformer-class.md)|`transformer` 傳訊區塊是多來源的單一目標排序 `propagator_block`，可以存放無限個不同類型訊息。|
|[unbounded_buffer 類別](unbounded-buffer-class.md)|`unbounded_buffer` 傳訊區塊是多目標、多來源的排序 `propagator_block`，能夠存放無限個訊息。|
|[unsupported_os 類別](unsupported-os-class.md)|這個類別會描述使用不支援的作業系統時擲回的例外狀況。|

### <a name="structures"></a>結構

|名稱|描述|
|----------|-----------------|
|[DispatchState 結構](dispatchstate-structure.md)|`DispatchState` 結構用來將狀態傳輸至 `IExecutionContext::Dispatch` 方法。 它描述在 `IExecutionContext` 介面上叫用 `Dispatch` 方法的情況。|
|[IExecutionContext 結構](iexecutioncontext-structure.md)|執行內容的介面，可於指定的虛擬處理器上執行，也可以合作方式切換內容。|
|[IExecutionResource 結構](iexecutionresource-structure.md)|硬體執行緒的抽象概念。|
|[IResourceManager 結構](iresourcemanager-structure.md)|並行執行階段資源管理員的介面。 這是排程器用來與資源管理員通訊的介面。|
|[IScheduler 結構](ischeduler-structure.md)|工作排程器抽象概念的介面。 並行執行階段的資源管理員會使用這個介面與工作排程器通訊。|
|[ISchedulerProxy 結構](ischedulerproxy-structure.md)|排程器用來與並行執行階段的資源管理員通訊，以協調資源配置的介面。|
|[IThreadProxy 結構](ithreadproxy-structure.md)|執行緒的抽象概念。 視您所建立之排程器的 `SchedulerType` 原則機碼而定，資源管理員會授與您支援一般 Win32 執行緒或可使用者模式排程 (UMS) 執行緒的執行緒 Proxy。 安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。|
|[ITopologyExecutionResource 結構](itopologyexecutionresource-structure.md)|資源管理員所定義的執行資源介面。|
|[ITopologyNode 結構](itopologynode-structure.md)|資源管理員所定義的拓撲節點介面。 節點可包含一個或多個執行資源。|
|[IUMSCompletionList 結構](iumscompletionlist-structure.md)|代表 UMS 完成清單。 當 UMS 執行緒封鎖時，會分派排程器的指定排程內容，以決定封鎖原始執行緒時要在基礎虛擬處理器根排程的內容。 原始執行緒解除封鎖時，作業系統會將它佇列到可透過此介面存取的完成清單中。 排程器可以在指派的排程內容或其搜尋工作的其他任何位置查詢完成清單。|
|[IUMSScheduler 結構](iumsscheduler-structure.md)|工作排程器抽象概念的介面，需要並行執行階段的資源管理員將可使用者模式排程的 (UMS) 執行緒傳遞給它。 資源管理員會使用這個介面與 UMS 執行緒排程器進行通訊。 `IUMSScheduler` 介面繼承自 `IScheduler` 介面。|
|[IUMSThreadProxy 結構](iumsthreadproxy-structure.md)|執行緒的抽象概念。 如果您想要將可使用者模式排程 (UMS) 的執行緒授與給排程器，請將排程器原則項目 `SchedulerKind` 的值設為 `UmsThreadDefault`，並實作 `IUMSScheduler` 介面。 只有安裝 Windows 7 (含以上) 版本的 64 位元作業系統支援 UMS 執行緒。|
|[IUMSUnblockNotification 結構](iumsunblocknotification-structure.md)|代表資源管理員發出的通知，其中說明遭封鎖並觸發傳回給排程器所指派之排程內容的執行緒 Proxy 已解除鎖定，而且已準備好進行排程。 若重新排程從 `GetContext` 方法傳回之執行緒 Proxy 的相關執行內容，則此介面不正確。|
|[IVirtualProcessorRoot 結構](ivirtualprocessorroot-structure.md)|執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。|
|[scheduler_interface 結構](scheduler-interface-structure.md)|排程器介面|
|[scheduler_ptr 結構 (並行執行階段)](scheduler-ptr-structure-concurrency-runtime.md)|代表排程器的指標。 這個類別存在，以允許使用 shared_ptr 或只是簡單參考使用原始指標的共用的存留期的規格。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|`agent` 的有效狀態。|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|可以使用代理程式程式庫所提供之追蹤功能追蹤的事件類型|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|可以使用並行執行階段所提供的追蹤功能追蹤的事件類型。|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|事件類型的追蹤旗標。|
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|內含內容之關鍵區域的類型。|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|`DynamicProgressFeedback` 原則用來描述要根據從排程器收集到的統計資訊重新平衡排程器的資源，或者只要根據透過 `IVirtualProcessorRoot` 介面上的 `Activate` 和 `Deactivate` 方法呼叫進出閒置狀態的虛擬處理器。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)。|
|[join_type](concurrency-namespace-enums.md#join_type)|`join` 傳訊區塊的類型。|
|[message_status](concurrency-namespace-enums.md#message_status)|`message` 物件對區塊供應項目的有效回應。|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|描述排程器行為方面的原則機碼。 每個原則項目由一個機碼值組描述。 如需排程器排程器原則和其影響的相關詳細資訊，請參閱[工作排程器](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)。|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|`SchedulerKind` 原則用來描述排程器應用於基礎執行內容的執行緒類型。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)。|
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|`SchedulingProtocol` 原則用於描述排程器將使用的排程演算法。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)。|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|用來表示執行緒 Proxy 所處的狀態 (當它正在執行將合作內容切換到不同的執行緒 Proxy 時)。|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|描述 `task_group` 或 `structured_task_group` 物件的執行狀態。 等待預定工作群組完成工作的許多方法，會傳回這個類型的值。|
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|由 `WinRTInitialization` 原則用來描述 Windows 執行階段是否會在執行 Windows 8 (含) 以後版本作業系統之應用程式的排程器執行緒上初始化，以及如何進行初始化。 如需有關可用排程器原則的詳細資訊，請參閱 < [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[Alloc 函式](concurrency-namespace-functions.md#alloc)|會透過並行執行階段的快取子配置器指定的大小，來配置記憶體區塊。|
|[asend 函式](concurrency-namespace-functions.md#asend)|多載。 非同步傳送作業，會排程工作將資料傳播到目標區塊。|
|[cancel_current_task 函式](concurrency-namespace-functions.md#cancel_current_task)|取消目前執行的工作。 這個函式可以從工作主體內呼叫，以中止工作執行並導致它進入 `canceled` 狀態。<br /><br /> 如果不是在 `task` 的主體中，這就不是支援呼叫這個函式的情況。 這樣做會在應用程式中導致未定義的行為，例如當機或停止回應。|
|[create_async 函式](concurrency-namespace-functions.md#create_async)|以使用者提供的 Lambda 或函式物件為基礎，建立 Windows 執行階段非同步建構。 根據傳遞至方法的 Lambda 簽章，`create_async` 的傳回型別是下列其中一個：`IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^` 或 `IAsyncOperationWithProgress<TResult, TProgress>^`。|
|[create_task 函式](concurrency-namespace-functions.md#create_task)|多載。 建立 PPL[任務](task-class.md)物件。 您可以在任何會使用工作建構函式的地方使用 `create_task`。 這主要是為了方便起見而提供，因為它允許在建立工作時使用 `auto` 關鍵字。|
|[CreateResourceManager 函式](concurrency-namespace-functions.md#createresourcemanager)|傳回代表並行執行階段資源管理員單一執行個體的介面。 資源管理員會負責將資源指派給想要與彼此相互合作的排程器。|
|[DisableTracing 函式](concurrency-namespace-functions.md#disabletracing)|停用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已移除註冊而被取代。|
|[EnableTracing 函式](concurrency-namespace-functions.md#enabletracing)|啟用並行執行階段中的追蹤。 根據預設，這個函式因為 ETW 追蹤已開啟而被取代。|
|[Free 函式](concurrency-namespace-functions.md#free)|釋放先前由 `Alloc` 方法配置的記憶體區塊至並行執行階段的快取子配置器。|
|[get_ambient_scheduler 函式 （並行執行階段）](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId 函式](concurrency-namespace-functions.md#getexecutioncontextid)|傳回可指派給實作 `IExecutionContext` 介面之執行內容的唯一識別碼。|
|[GetOSVersion 函式](concurrency-namespace-functions.md#getosversion)|傳回作業系統版本。|
|[GetProcessorCount 函式](concurrency-namespace-functions.md#getprocessorcount)|傳回基礎系統上的硬體執行緒數目。|
|[GetProcessorNodeCount 函式](concurrency-namespace-functions.md#getprocessornodecount)|傳回基礎系統上的 NUMA 節點或處理器套件數目。|
|[GetSchedulerId 函式](concurrency-namespace-functions.md#getschedulerid)|傳回可指派給實作 `IScheduler` 介面之排程器的唯一識別碼。|
|[interruption_point 函式](concurrency-namespace-functions.md#interruption_point)|建立取消的中斷點。 如果這個函式呼叫的內容正在取消，則會擲出中止目前執行之平行工作執行的內部例外狀況。 如果取消不在進行中，函式不會執行任何動作。|
|[is_current_task_group_canceling 函式](concurrency-namespace-functions.md#is_current_task_group_canceling)|傳回指示，以說明目前正以內嵌方式在目前內容上執行的工作群組是否正在取消 (或即將取消)。 請注意，如果目前沒有任何工作群組以內嵌方式在目前的內容上執行，會傳回 `false`。|
|[make_choice 函式](concurrency-namespace-functions.md#make_choice)|多載。 從選擇性的 `choice` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。|
|[make_greedy_join 函式](concurrency-namespace-functions.md#make_greedy_join)|多載。 從選擇性的 `greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。|
|[make_join 函式](concurrency-namespace-functions.md#make_join)|多載。 從選擇性的 `non_greedy multitype_join` 或 `Scheduler` 和兩個或多個輸入來源建立 `ScheduleGroup` 傳訊區塊。|
|[make_task 函式](concurrency-namespace-functions.md#make_task)|建立 `task_handle` 物件的 Factory 方法。|
|[parallel_buffered_sort 函式](concurrency-namespace-functions.md#parallel_buffered_sort)|多載。 將在指定範圍中的項目排列成非遞減順序，或是依據二元述詞指定的順序準則以平行方式排列。 這個函式語意與 `std::sort` 類似：皆是以比較為基礎、不穩定、就地排序的；差別為它需要 `O(n)` 額外的空間，且必須預設初始化需排序的項目。|
|[parallel_for 函式](concurrency-namespace-functions.md#parallel_for)|多載。 `parallel_for` 會逐一查看某個範圍的索引，並以平行方式在每個反覆項目上執行使用者提供的函式。|
|[parallel_for_each 函式](concurrency-namespace-functions.md#parallel_for_each)|多載。 `parallel_for_each` 會平行套用指定的函式到範圍內的每個項目。 在語意上，它相當於 `std` 命名空間中的 `for_each` 函式，但項目的反覆項目會平行執行，而且不會指定反覆項目的順序。 `_Func` 引數必須支援 `operator()(T)` 形式的函式呼叫運算子，其中 `T` 參數是要逐一查看之容器的項目類型。|
|[parallel_invoke 函式](concurrency-namespace-functions.md#parallel_invoke)|多載。 平行執行提供作為參數的函式物件，並加以封鎖直到完成執行為止。 函式物件可能是 Lambda 運算式、函式指標，或是支援函式呼叫運算子與簽章 `void operator()()` 版本的任何物件。|
|[parallel_radixsort 函式](concurrency-namespace-functions.md#parallel_radixsort)|多載。 使用基數排序演算法，將指定範圍內的項目排列成非遞減順序。 這是一個穩定的排序函式，其需要可將項目排序成不帶正負號的整數機碼的投影函式。 要排序的項目都必須進行預設初始化。|
|[parallel_reduce 函式](concurrency-namespace-functions.md#parallel_reduce)|多載。 以平行方式，透過計算後繼元素的部分總和來計算在一定範圍內所有項目的總和，或是計算部分後繼結果 (取得方式是使用指定的二進位運算而非總和運算得出) 的結果。 `parallel_reduce` 語意與 `std::accumulate` 類似；不同的是，它需要關聯的二進位運算，而且需要識別值而不是初始值。|
|[parallel_sort 函式](concurrency-namespace-functions.md#parallel_sort)|多載。 將在指定範圍中的項目排列成非遞減順序，或是依據二元述詞指定的順序準則以平行方式排列。 這個函式語意與 `std::sort` 類似，皆是以比較為基礎、不穩定、就地排序的。|
|[parallel_transform 函式](concurrency-namespace-functions.md#parallel_transform)|多載。 以平行方式，將指定的函式物件套用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。 此函式在語意上等於 `std::transform`。|
|[接收函式](concurrency-namespace-functions.md#receive)|多載。 一般接收實作，可讓內容等候來自一個來源的資料，並且篩選所接受的值。|
|[run_with_cancellation_token 函式](concurrency-namespace-functions.md#run_with_cancellation_token)|在指定的取消語彙基元內容中立即和同步地執行函式物件。|
|[send 函式](concurrency-namespace-functions.md#send)|多載。 同步傳送作業，其會等候直到目標接受或拒絕訊息。|
|[set_ambient_scheduler 函式 （並行執行階段）](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources 函式](concurrency-namespace-functions.md#set_task_execution_resources)|多載。 依據指定的同質性集，限制並行執行階段之內部背景工作執行緒使用的執行資源。<br /><br /> 只有在資源管理員建立之前，或在兩個資源管理員存留期之間，才能有效地呼叫這個方法。 只要資源管理員不在引動過程期間，即可多次叫用此函式。 在同質性限制設定之後，直到下次有效呼叫 `set_task_execution_resources` 方法之前，該限制會持續有效。<br /><br /> 提供的同質性遮罩不需為處理序同質性遮罩的子集。 您可視需要更新處理序的同質性遮罩。|
|[swap 函式](concurrency-namespace-functions.md#swap)|交換兩個 `concurrent_vector` 物件的項目。|
|[task_from_exception 函式 （並行執行階段）](concurrency-namespace-functions.md#task_from_exception)||
|[task_from_result 函式 （並行執行階段）](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name 函式](concurrency-namespace-functions.md#trace_agents_register_name)|將指定的名稱與 ETW 追蹤的訊息區塊或代理程式產生關聯。|
|[try_receive 函式](concurrency-namespace-functions.md#try_receive)|多載。 一般嘗試-接收實作，可讓內容尋找來自特定一個來源的資料，並且篩選所接受的值。 如果資料還沒準備好，方法會傳回 false。|
|[wait 函式](concurrency-namespace-functions.md#wait)|暫停目前的內容達指定的時間長度。|
|[when_all 函式](concurrency-namespace-functions.md#when_all)|建立工作，這個工作將會在當做引數提供的所有工作都已順利完成時成功完成。|
|[when_any 函式](concurrency-namespace-functions.md#when_any)|多載。 建立工作，這個工作會在當做引數提供的所有工作都順利完成時，順利完成。|

### <a name="operators"></a>運算子

|名稱|描述|
|----------|-----------------|
|[operator!=](concurrency-namespace-operators.md#operator_neq)|測試運算子左邊的 `concurrent_vector` 物件是否不等於右邊的 `concurrent_vector` 物件。|
|[operator&&](concurrency-namespace-operators.md#operator_amp_amp)|多載。 建立工作，這個工作將會在兩個當做引數提供的工作都已順利完成時成功完成。|
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|多載。 建立工作，這個工作將會在兩個當做引數提供的任一工作已順利完成時成功完成。|
|[operator<](concurrency-namespace-operators.md#operator_lt)|測試運算子左邊的 `concurrent_vector` 物件是否小於右邊的 `concurrent_vector` 物件。|
|[operator<=](concurrency-namespace-operators.md#operator_lt_eq)|測試運算子左邊的 `concurrent_vector` 物件是否小於或等於右邊的 `concurrent_vector` 物件。|
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|測試運算子左邊的 `concurrent_vector` 物件是否等於右邊的 `concurrent_vector` 物件。|
|[operator>](concurrency-namespace-operators.md#operator_gt)|測試運算子左邊的 `concurrent_vector` 物件是否大於右邊的 `concurrent_vector` 物件。|
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|測試運算子左邊的 `concurrent_vector` 物件是否大於或等於右邊的 `concurrent_vector` 物件。|

### <a name="constants"></a>常數

|名稱|描述|
|----------|-----------------|
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|分類 GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07})，描述在並行執行階段由代理程式程式庫引發的 ETW 事件。|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|分類 GUID，描述直接與工作相關之並行執行階段引發的 ETW 事件。|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|目前執行階段的 ETW 提供者 GUID。|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|指出支援 Visual Studio 2010 中定義的資源管理員介面。|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|分類 GUID，描述其他分類未特定描述之並行執行階段引發的 ETW 事件。|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|分類 GUID，描述直接與內容相關之並行執行階段引發的 ETW 事件。|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|值，表示等候應該永遠不會逾時。|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|值，表示等候已逾時。|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|原則機碼 `ContextPriority` 的特殊值，代表排程器中所有內容的執行緒優先順序應該與建立排程器之執行緒的優先順序相同。|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|分類 GUID，描述直接與鎖定相關之並行執行階段引發的 ETW 事件。|
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|原則機碼 `MinConcurrency` 和 `MaxConcurrency` 的特殊值。 預設值是在沒有其他條件約束的情況下，電腦上的硬體執行緒數目。|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|分類 GUID，描述直接與 `parallel_for_each` 函式使用方式相關之並行執行階段引發的 ETW 事件。|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|分類 GUID，描述直接與 `parallel_for` 函式使用方式相關之並行執行階段引發的 ETW 事件。|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|分類 GUID，描述直接與 `parallel_invoke` 函式使用方式相關之並行執行階段引發的 ETW 事件。|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|分類 GUID，描述直接與資源管理員相關之並行執行階段引發的 ETW 事件。|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|分類 GUID，描述直接與排程群組相關之並行執行階段引發的 ETW 事件。|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|分類 GUID，描述直接與排程器活動相關之並行執行階段引發的 ETW 事件。|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|分類 GUID，描述直接與虛擬處理器相關之並行執行階段引發的 ETW 事件。|

## <a name="requirements"></a>需求

**標頭：** agents.h、 concrt.h、 concrtrm.h、 concurrent_priority_queue.h、 concurrent_queue.h、 concurrent_unordered_map.h、 concurrent_unordered_set.h、 concurrent_vector.h、 internal_concurrent_hash.h、 internal_split_ordered_list.h、 ppl.h、 pplcancellation_token.h、 pplconcrt.h、 pplinterface.h、 ppltasks.h

## <a name="see-also"></a>另請參閱

[參考資料](reference-concurrency-runtime.md)
