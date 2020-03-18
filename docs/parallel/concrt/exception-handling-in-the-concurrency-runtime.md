---
title: 並行執行階段的例外狀況處理
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 4c7fee363da023b9252471a35aaecd262a55f17c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422245"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>並行執行階段的例外狀況處理

並行執行階段會使用C++例外狀況處理來傳達多種類型的錯誤。 這些錯誤包括不正確的執行時間使用、執行階段錯誤（例如無法取得資源），以及您提供給工作和工作組的工作函式中發生的錯誤。 當工作或工作組擲回例外狀況時，執行時間會保存該例外狀況，並將其封送處理至等候工作或工作組完成的內容。 針對輕量工作和代理程式之類的元件，執行時間不會為您管理例外狀況。 在這些情況下，您必須執行自己的例外狀況處理機制。 本主題描述執行時間如何處理工作、工作組、羽量級工作和非同步代理程式所擲回的例外狀況，以及如何回應應用程式中的例外狀況。

## <a name="key-points"></a>重點

- 當工作或工作組擲回例外狀況時，執行時間會保存該例外狀況，並將其封送處理至等候工作或工作組完成的內容。

- 可能的話，請在每次呼叫[concurrency：： task：： get](reference/task-class.md#get)和[concurrency：： task：： wait](reference/task-class.md#wait)時，使用 `try`/`catch` 區塊來處理您可以復原的錯誤。 如果工作擲回例外狀況，而且工作、其中一個接續或主要應用程式未攔截到例外狀況，則執行時間會終止應用程式。

- 以工作為基礎的接續一律會執行;不論 antecedent 工作成功完成、擲回例外狀況，還是已取消。 如果 antecedent 工作擲回或取消，就不會執行以值為基礎的接續。

- 因為以工作為基礎的接續一律會執行，請考慮是否要在接續鏈結尾處新增以工作為基礎的接續。 這有助於確保您的程式碼會觀察到所有例外狀況。

- 當您呼叫[concurrency：： task：： get](reference/task-class.md#get)並取消工作時，執行時間會擲回[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md) 。

- 執行時間不會管理輕量工作和代理程式的例外狀況。

## <a name="top"></a>本檔中的

- [工作和接續](#tasks)

- [工作組和平行演算法](#task_groups)

- [執行時間擲回的例外狀況](#runtime)

- [多個例外狀況](#multiple)

- [取消](#cancellation)

- [輕量型工作](#lwts)

- [非同步代理程式](#agents)

## <a name="tasks"></a>工作和接續

本節說明執行時間如何處理[concurrency：： task](../../parallel/concrt/reference/task-class.md)物件及其接續所擲回的例外狀況。 如需工作和接續模型的詳細資訊，請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

當您在傳遞給 `task` 物件的工作函式主體中擲回例外狀況時，執行時間會儲存該例外狀況，並將其封送處理至呼叫[concurrency：： task：： get](reference/task-class.md#get)或[concurrency：： task：： wait](reference/task-class.md#wait)的內容。 檔工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則會描述以工作為基礎與以值為基礎的接續，但總結而言，以值為基礎的接續會採用類型 `T` 的參數，而以工作為基礎的接續會接受 `task<T>`類型的參數。 如果擲回的工作具有一或多個以值為基礎的接續，則這些接續不會排程執行。 下列範例可說明此行為：

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

以工作為基礎的接續可讓您處理 antecedent 工作所擲回的任何例外狀況。 以工作為基礎的接續一律會執行;工作是否已順利完成、擲回例外狀況，或已取消。 當工作擲回例外狀況時，其以工作為基礎的接續會排程執行。 下列範例顯示的工作一律會擲回。 此工作有兩個接續;一個是以值為基礎，另一個則是以工作為基礎。 以工作為基礎的例外狀況一律會執行，因此可以攔截 antecedent 工作擲回的例外狀況。 當範例等候兩個接續完成時，就會再次擲回例外狀況，因為當呼叫 `task::get` 或 `task::wait` 時，一律會擲回工作例外狀況。

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

建議您使用以工作為基礎的接續來攔截您能夠處理的例外狀況。 因為以工作為基礎的接續一律會執行，請考慮是否要在接續鏈結尾處新增以工作為基礎的接續。 這有助於確保您的程式碼會觀察到所有例外狀況。 下列範例顯示以值為基礎的基本接續鏈。 鏈中的第三個工作會擲回，因此不會執行接在其後面的任何以值為基礎的接續。 不過，最後一個接續是以工作為基礎，因此一定會執行。 這最後一個接續會處理第三個工作擲回的例外狀況。

我們建議您攔截所能採取的最特定例外狀況。 如果您沒有要攔截的特定例外狀況，您可以省略這個最終以工作為基礎的接續。 任何例外狀況都將保持未處理狀態，並可終止應用程式。

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> 您可以使用[concurrency：： task_completion_event：： set_exception](../../parallel/concrt/reference/task-completion-event-class.md)方法，將例外狀況與工作完成事件產生關聯。 檔工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則會更詳細地描述[concurrency：： task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)類別。

[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)是與 `task`相關的重要執行時間例外狀況類型。 當您呼叫 `task::get` 並取消工作時，執行時間會擲回 `task_canceled`。 （相反地，`task::wait` 會傳回[task_status：：已取消](reference/concurrency-namespace-enums.md#task_group_status)，且不會擲回。）您可以從以工作為基礎的接續或呼叫 `task::get`來攔截和處理這個例外狀況。 如需工作取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

> [!CAUTION]
> 永遠不會從您的程式碼擲回 `task_canceled`。 請改為呼叫[concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) 。

如果工作擲回例外狀況，而且工作、其中一個接續或主要應用程式未攔截到例外狀況，則執行時間會終止應用程式。 如果您的應用程式損毀，您可以設定 Visual Studio C++在擲回例外狀況時中斷。 在您診斷未處理之例外狀況的位置之後，請使用以工作為基礎的接續來處理它。

本檔中[的運行](#runtime)時間所擲回的例外狀況一節將說明如何更詳細地使用執行時間例外狀況。

[[靠上](#top)]

## <a name="task_groups"></a>工作組和平行演算法

本節說明執行時間如何處理工作組所擲回的例外狀況。 本節也適用于並行處理演算法（例如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)），因為這些演算法會建置於工作組上。

> [!CAUTION]
> 請確定您瞭解例外狀況對相依工作的影響。 如需有關如何搭配工作或平行演算法使用例外狀況處理的建議做法，請參閱平行模式程式庫主題中的最佳作法中的[瞭解取消和例外狀況處理如何影響物件銷毀](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)一節。

如需工作組的詳細資訊，請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

當您在傳遞給[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件的工作函式主體中擲回例外狀況時，執行時間會儲存該例外狀況，並將其封送處理至呼叫 concurrency：： [task_group：： wait](reference/task-group-class.md#wait)、 [concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)、 [concurrency：： task_group：： run_and_wait](reference/task-group-class.md#run_and_wait)或[concurrency：](reference/structured-task-group-class.md#run_and_wait)： structured_task_group：： run_and_wait 的內容。 執行時間也會停止工作組中的所有作用中工作（包括子工作組中的工作），並捨棄尚未啟動的任何工作。

下列範例顯示擲回例外狀況的工作函式的基本結構。 此範例會使用 `task_group` 物件，以平行方式列印兩個 `point` 物件的值。 `print_point` work 函式會將 `point` 物件的值列印到主控台。 如果輸入值為 `NULL`，工作函式會擲回例外狀況。 執行時間會儲存此例外狀況，並將其封送處理至呼叫 `task_group::wait`的內容。

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

此範例會產生下列輸出。

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

如需在工作組中使用例外狀況處理的完整範例，請參閱[如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

[[靠上](#top)]

## <a name="runtime"></a>執行時間擲回的例外狀況

呼叫執行時間可能會導致例外狀況。 大部分的例外狀況類型（ [concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)和[concurrency：： operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)除外）表示程式設計錯誤。 這些錯誤通常是無法復原的，因此不應該由應用程式代碼攔截或處理。 我們建議您只在需要診斷程式設計錯誤時，才攔截或處理應用程式程式碼中無法復原的錯誤。 不過，若要瞭解執行時間所定義的例外狀況類型，可以協助您診斷程式設計錯誤。

例外狀況處理機制與執行時間擲回的例外狀況相同，是由工作函式所擲回的例外狀況。 例如， [concurrency：： receive](reference/concurrency-namespace-functions.md#receive)函式不會在指定的時間週期內收到訊息時，就會擲回 `operation_timed_out`。 如果 `receive` 在您傳遞至工作組的工作函式中擲回例外狀況，則執行時間會儲存該例外狀況，並將其封送處理至呼叫 `task_group::wait`、`structured_task_group::wait`、`task_group::run_and_wait`或 `structured_task_group::run_and_wait`的內容。

下列範例會使用[concurrency：:p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法，以平行方式執行兩個工作。 第一個工作會等候五秒，然後將訊息傳送至訊息緩衝區。 第二個工作會使用 `receive` 函式來等候三秒，以從相同的訊息緩衝區接收訊息。 如果 `receive` 函式在時間週期內未收到訊息，則會擲回 `operation_timed_out`。

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

此範例會產生下列輸出。

```Output
The operation timed out.
```

若要避免應用程式異常終止，請確定您的程式碼會在呼叫執行時間時處理例外狀況。 當您呼叫使用並行執行階段（例如協力廠商程式庫）的外部程式碼時，也會處理例外狀況。

[[靠上](#top)]

## <a name="multiple"></a>多個例外狀況

如果工作或平行演算法收到多個例外狀況，執行時間就只會將其中一個例外狀況封送處理至呼叫內容。 執行時間不保證它要封送處理的例外狀況。

下列範例會使用 `parallel_for` 演算法，將數位列印到主控台。 如果輸入值小於某個最小值或大於某個最大值，它就會擲回例外狀況。 在此範例中，多個工作函式可能會擲回例外狀況。

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

以下顯示此範例的範例輸出。

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[靠上](#top)]

## <a name="cancellation"></a>撤銷

並非所有例外狀況都表示發生錯誤。 例如，搜尋演算法可能會在找到結果時，使用例外狀況處理來停止其相關聯的工作。 如需如何在程式碼中使用取消機制的詳細資訊，請參閱[PPL 中的取消](../../parallel/concrt/cancellation-in-the-ppl.md)。

[[靠上](#top)]

## <a name="lwts"></a>輕量工作

輕量工作是您直接從[concurrency：：](../../parallel/concrt/reference/scheduler-class.md) schedule 物件排程的工作。 輕量工作的負擔比一般工作少。 不過，執行時間不會攔截輕量工作所擲回的例外狀況。 相反地，未處理的例外狀況處理常式會攔截例外狀況，其預設會終止進程。 因此，請在您的應用程式中使用適當的錯誤處理機制。 如需有關輕量工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[靠上](#top)]

## <a name="agents"></a>非同步代理程式

如同輕量工作，執行時間不會管理非同步代理程式所擲回的例外狀況。

下列範例示範在衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)的類別中處理例外狀況的一種方式。 這個範例會定義 `points_agent` 類別。 `points_agent::run` 方法會從訊息緩衝區讀取 `point` 物件，並將其列印至主控台。 如果 `run` 方法收到 `NULL` 指標，則會擲回例外狀況。

`run` 方法會將 `try`-`catch` 區塊中的所有工作括起來。 `catch` 區塊會將例外狀況儲存在訊息緩衝區中。 應用程式會在代理程式完成之後，從這個緩衝區讀取，檢查代理程式是否發生錯誤。

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

此範例會產生下列輸出。

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

由於 `try`-`catch` 區塊存在於 `while` 迴圈以外，因此代理程式會在遇到第一個錯誤時結束處理。 如果 `try`-`catch` 區塊在 `while` 迴圈內，則代理程式會在錯誤發生後繼續。

這個範例會將例外狀況儲存在訊息緩衝區中，讓另一個元件可以在代理程式執行時監視其是否有錯誤。 這個範例使用[concurrency：： single_assignment](../../parallel/concrt/reference/single-assignment-class.md)物件來儲存錯誤。 在代理程式處理多個例外狀況的情況下，`single_assignment` 類別只會儲存傳遞給它的第一個訊息。 若只要儲存最後一個例外狀況，請使用[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別。 若要儲存所有例外狀況，請使用[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)類別。 如需這些訊息區塊的詳細資訊，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

如需非同步代理程式的詳細資訊，請參閱[非同步代理](../../parallel/concrt/asynchronous-agents.md)程式。

[[靠上](#top)]

## <a name="summary"></a> 摘要

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)
