---
title: 並行執行階段的例外狀況處理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9490fcbd765f277030c235a09d5b6d86d6522676
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405199"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>並行執行階段的例外狀況處理

並行執行階段使用 c + + 例外狀況處理來進行通訊的許多類型的錯誤。 這些錯誤會包括在您提供給工作和工作群組的工作函式中使用無效的執行階段失敗，無法取得資源，例如執行階段錯誤，所發生的錯誤。 當工作或工作群組擲回例外狀況時，執行階段會保留該例外狀況，並將它封送處理至等候工作或工作群組完成的內容。 輕量型工作等代理程式的元件，執行階段不會管理您的例外狀況。 在這些情況下，您必須實作您自己的例外狀況處理機制。 本主題說明執行階段如何處理工作、 工作群組、 輕量型工作和非同步代理程式，所擲回的例外狀況，以及如何回應您的應用程式中的例外狀況。

## <a name="key-points"></a>重點

- 當工作或工作群組擲回例外狀況時，執行階段會保留該例外狀況，並將它封送處理至等候工作或工作群組完成的內容。

- 如果可能的話，括住每次呼叫[concurrency](reference/task-class.md#get)並[concurrency::task::wait](reference/task-class.md#wait)具有`try` / `catch`區塊來處理您可以復原的錯誤從。 如果工作擲回例外狀況和工作中，其接續或主要的應用程式的其中一個未攔截的例外狀況，執行階段就會終止應用程式。

- 以工作為基礎的接續一律會執行;不論是否已順利完成，前項工作擲回例外狀況，或已取消。 值為基礎的接續不會執行，如果前項工作擲回，或取消。

- 因為工作為基礎的接續一律執行，請考慮是否要接續鏈結的結尾加入以工作為基礎的接續。 這可協助確保您的程式碼觀察到所有例外狀況。

- 執行階段會擲回[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)當您呼叫[concurrency](reference/task-class.md#get)並取消該工作。

- 執行階段不會管理輕量型工作和代理程式的例外狀況。

##  <a name="top"></a> 在這份文件

- [工作和接續工作](#tasks)

- [工作群組和平行演算法](#task_groups)

- [執行階段擲回例外狀況](#runtime)

- [多個例外狀況](#multiple)

- [取消](#cancellation)

- [輕量型工作](#lwts)

- [非同步代理程式](#agents)

##  <a name="tasks"></a> 工作和接續工作

本章節描述執行階段如何處理所擲回的例外狀況[concurrency:: task](../../parallel/concrt/reference/task-class.md)物件和其接續。 如需有關工作和接續模型的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

當您擲回例外狀況的工作函式傳遞至內`task`物件，執行階段會儲存該例外狀況，並將它封送處理至呼叫內容[concurrency](reference/task-class.md#get)或[並行::task:: wait](reference/task-class.md#wait)。 文件[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)描述工作為基礎，與值為基礎的接續，但若要總結來說，值為基礎的接續會採用類型參數的`T`和以工作為基礎的接續會採用參數的型別`task<T>`. 如果工作擲回有一或多個值為基礎的接續，未排定接續執行。 下列範例可說明此行為：

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

以工作為基礎的接續可讓您處理由前項工作擲回任何例外狀況。 以工作為基礎的接續一律會執行;不論是否已順利完成，工作擲回例外狀況，或已取消。 當工作擲回例外狀況時，其以工作為基礎的接續會排定執行。 下列範例顯示一律會擲回的工作。 工作有兩個接續;一個值為基礎，另一個則是以工作為基礎。 以工作為基礎的例外狀況一定會執行，並因此可以攔截前項工作所擲回的例外狀況。 當此範例會等到完成這兩個接續時，例外狀況時再次因為工作一律擲回例外狀況時`task::get`或`task::wait`呼叫。

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

我們建議使用以工作為基礎的接續攔截，就可以處理的例外狀況。 因為工作為基礎的接續一律執行，請考慮是否要接續鏈結的結尾加入以工作為基礎的接續。 這可協助確保您的程式碼觀察到所有例外狀況。 下列範例示範基本的值為基礎的接續鏈結。 鏈結中的第三個工作擲回，並因此不會執行任何值為基礎的接續在它後面。 不過，最後的接續是以工作為基礎，並因此一律會執行。 這個最後的接續會處理第三項工作所擲回的例外狀況。

我們建議您攔截您可以最特定例外狀況。 如果您沒有來攔截特定例外狀況，您可以省略此最終工作為基礎的接續。 任何例外狀況仍未處理，且可以終止應用程式。

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
>  您可以使用[concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md)例外狀況相關聯的工作完成事件的方法。 文件[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)描述[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)更詳細的類別。

[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)是與相關的重要的執行階段例外狀況類型`task`。 執行階段會擲回`task_canceled`當您呼叫`task::get`並取消該工作。 (相反地，`task::wait`會傳回[task_status:: canceled](reference/concurrency-namespace-enums.md#task_group_status)並不會擲回。)您可以攔截並處理這個例外狀況，從以工作為基礎的接續，或當您呼叫`task::get`。 如需有關工作取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

> [!CAUTION]
>  永遠不會從您的程式碼擲回 `task_canceled`。 呼叫[concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)改。

如果工作擲回例外狀況和工作中，其接續或主要的應用程式的其中一個未攔截的例外狀況，執行階段就會終止應用程式。 如果您的應用程式損毀，您可以設定 Visual Studio c + + 例外狀況會擲回時中斷。 診斷處理的例外狀況的位置之後，使用以工作為基礎的接續來處理它。

一節[由執行階段擲回的例外狀況](#runtime)本文件說明如何使用更詳細的執行階段例外狀況。

[[靠上](#top)]

##  <a name="task_groups"></a> 工作群組和平行演算法

本章節描述執行階段如何處理工作群組所擲回的例外狀況。 本節也適用於平行演算法這類[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，因為這些演算法會建置在工作群組上。

> [!CAUTION]
>  請確定您已了解例外狀況都有相依的工作的效果。 如需有關如何使用例外狀況處理的工作或平行演算法的建議作法，請參閱[了解如何取消和例外狀況處理會影響的物件解構](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)一節中以平行方式的最佳作法模式程式庫的主題。

如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

當您擲回例外狀況的工作函式傳遞至內[concurrency:: task_group](reference/task-group-class.md)或是[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，執行階段會儲存該例外狀況，並將它封送處理若要呼叫的內容[2&gt;concurrency::task_group::wait&lt;2](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [run_and_wait](reference/task-group-class.md#run_and_wait)，或[run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 執行階段也會停止所有作用中工作 （包括子工作群組） 的工作群組中，並會捨棄任何尚未開始的工作。

下列範例顯示工作函式會擲回例外狀況的基本的結構。 此範例會使用`task_group`列印兩個值的物件`point`以平行方式的物件。 `print_point`工作函式會列印值`point`至主控台的物件。 如果輸入的值為工作函式擲回例外狀況`NULL`。 執行階段會儲存此例外狀況，並將它封送處理至呼叫內容`task_group::wait`。

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

此範例會產生下列輸出。

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

如需使用工作群組中處理的例外狀況的完整範例，請參閱 <<c0> [ 如何： 使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

[[靠上](#top)]

##  <a name="runtime"></a> 執行階段擲回例外狀況

例外狀況可能起因於執行階段呼叫。 大部分的例外狀況類型，除了[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)並[concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)，指出程式設計錯誤。 這些錯誤通常是無法復原，並因此不應該攔截或處理應用程式程式碼。 我們建議您只攔截或無法復原的錯誤處理應用程式程式碼中，當您要診斷的程式設計錯誤。 不過，了解例外狀況類型所定義的執行階段可協助您診斷的程式設計錯誤。

例外狀況處理機制是相同的執行階段為工作函式所擲回的例外狀況擲回的例外狀況。 例如， [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式會擲回`operation_timed_out`時未收到一則訊息中指定的時段。 如果`receive`在工作函式擲回例外狀況，您傳遞至工作群組，執行階段會儲存該例外狀況，並將它封送處理至呼叫內容`task_group::wait`， `structured_task_group::wait`， `task_group::run_and_wait`，或`structured_task_group::run_and_wait`。

下列範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法以平行方式執行兩項工作。 第一項工作會等待 5 秒鐘，然後將訊息傳送至訊息緩衝區。 第二項工作會使用`receive`等待三秒鐘，即可從相同的訊息緩衝區接收訊息的函式。 `receive`函式會擲回`operation_timed_out`如果它未接收到訊息中的時間週期。

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

此範例會產生下列輸出。

```Output
The operation timed out.
```

若要避免您的應用程式異常終止，請確定您的程式碼在執行階段會呼叫時，會處理例外狀況。 當您呼叫外部程式碼會使用並行執行階段，比方說，協力廠商程式庫時，也可以處理的例外狀況。

[[靠上](#top)]

##  <a name="multiple"></a> 多個例外狀況

如果工作或平行演算法收到多個例外狀況，執行階段封送處理這些例外狀況至呼叫內容的其中之一。 執行階段不保證它封送處理的例外狀況。

下列範例會使用`parallel_for`列印至主控台的數字的演算法。 它會擲回例外狀況，如果輸入的值小於某些最小值或大於某些最大值。 在此範例中，多個工作函式可以擲回例外狀況。

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

下圖顯示此範例的範例輸出。

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[靠上](#top)]

##  <a name="cancellation"></a> 取消作業

並非所有例外狀況表示發生錯誤。 比方說，搜尋演算法可能會停止其相關聯的工作，當它找到結果時使用例外狀況處理。 如需如何使用程式碼中的取消機制的詳細資訊，請參閱[PPL 中的取消](../../parallel/concrt/cancellation-in-the-ppl.md)。

[[靠上](#top)]

##  <a name="lwts"></a> 輕量型工作

輕量型工作是直接從排程的工作[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)物件。 輕量型工作會執行較少的額外負荷比一般的工作。 不過，執行階段不會攔截輕量型工作所擲回的例外狀況。 相反地，未處理的例外狀況處理常式，它預設會終止處理序會攔截例外狀況。 因此，在您的應用程式中使用適當的錯誤處理機制。 如需輕量型工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[靠上](#top)]

##  <a name="agents"></a> 非同步代理程式

輕量型工作，例如執行階段不會管理非同步代理程式所擲回的例外狀況。

下列範例示範衍生自的類別中處理例外狀況的方法之一[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 這個範例會定義`points_agent`類別。 `points_agent::run`方法會讀取`point`訊息緩衝區的物件，並列印到主控台。 `run`方法擲回例外狀況，如果收到`NULL`指標。

`run`方法周圍中的所有工作`try` - `catch`區塊。 `catch`區塊訊息緩衝區中儲存例外狀況。 應用程式會檢查是否的代理程式遇到錯誤藉由這個緩衝區讀取代理程式完成之後。

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

此範例會產生下列輸出。

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

因為`try` - `catch`區塊存在於外部`while`迴圈，代理程式就會結束處理時遇到的第一個錯誤。 如果`try` - `catch`區塊內是`while`迴圈中，代理程式會繼續之後發生錯誤。

這個範例會在訊息緩衝區中儲存例外狀況，好讓它執行時，另一個元件可以監視錯誤的代理程式。 這個範例會使用[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)儲存錯誤的物件。 在案例中，代理程式會處理多個例外狀況，`single_assignment`類別會儲存在只有第一個訊息傳遞給它。 若要儲存的最後一個例外狀況，使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別。 若要儲存的所有例外狀況，使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)類別。 如需有關這些訊息區塊的詳細資訊，請參閱 <<c0> [ 非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

如需有關非同步代理程式的詳細資訊，請參閱 <<c0> [ 非同步代理程式](../../parallel/concrt/asynchronous-agents.md)。

[[靠上](#top)]

##  <a name="summary"></a> 總結

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)<br/>
[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

