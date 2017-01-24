---
title: "並行執行階段的例外狀況處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輕量型工作, 例外狀況處理 [並行執行階段]"
  - "例外狀況處理 [並行執行階段]"
  - "結構化工作群組, 例外狀況處理 [並行執行階段]"
  - "代理程式, 例外狀況處理 [並行執行階段]"
  - "工作群組, 例外狀況處理 [並行執行階段]"
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: 29
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 並行執行階段的例外狀況處理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

並行執行階段會使用 C\+\+ 例外狀況處理來溝通許多類型的錯誤。  這些錯誤包括執行階段的無效用法、如取得資源失敗之類的執行階段錯誤，以及在您提供給工作和工作群組的工作函式中發生的錯誤。  當工作或工作群組擲回例外狀況時，執行階段會保留該例外狀況，並將其封送處理至等候這個工作群組完成的內容。  執行階段並不會管理輕量型工作和代理程式這類元件的例外狀況。  在這些情況下，您必須實作自己的例外狀況處理機制。  本主題說明執行階段會如何處理由工作、工作群組、輕量型工作和非同步代理程式所擲回的例外狀況，以及如何在您的應用程式中回應例外狀況。  
  
## 重點  
  
-   當工作或工作群組擲回例外狀況時，執行階段會保留該例外狀況，並將其封送處理至等候這個工作群組完成的內容。  
  
-   如果可能，請圍繞每呼叫 [concurrency::task::get](../Topic/task::get%20Method.md) 和 [concurrency::task::wait](../Topic/task::wait%20Method.md) 以 `try`\/`catch` 區塊處理可復原的錯誤。  執行階段結束應用程式，如果工作擲回例外狀況，該例外狀況不是由工作、接續程式或主應用程式攔截。  
  
-   以工作的接續永遠執行；成功完成的前項工作，是否擲回例外狀況，或已取消並不重要。  如果前項工作擲回或取消，數值繼續無法執行。  
  
-   由於以工作的接續永遠執行，是否考慮將以工作的接續在接續鏈結結尾。  這有助於確保您的程式碼檢視所有例外狀況。  
  
-   執行階段會擲回 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) ，當您呼叫 [concurrency::task::get](../Topic/task::get%20Method.md) 時，該工作已取消。  
  
-   執行階段不處理輕量型工作和代理程式的例外狀況。  
  
##  <a name="top"></a> 本文內容  
  
-   [工作和接續](#tasks)  
  
-   [工作群組和平行演算法](#task_groups)  
  
-   [執行階段所擲回的例外狀況](#runtime)  
  
-   [多個例外狀況](#multiple)  
  
-   [取消](#cancellation)  
  
-   [輕量型工作](#lwts)  
  
-   [非同步代理程式](#agents)  
  
##  <a name="tasks"></a> 工作和接續  
 本節說明執行階段如何管理由 [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 物件及其接續所擲回的例外狀況。  如需工作和繼續模型的詳細資訊，請參閱 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 當您在傳遞至`task`物件的工作函式主體中擲回例外狀況時，執行階段會儲存該例外狀況，並將其呼叫[concurrency::task::get](../Topic/task::get%20Method.md) 或 [concurrency::task::wait](../Topic/task::wait%20Method.md)的內容。  [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 文件描述以工作為數值繼續，不過，總結來說，數值會繼續使用型别 `T` 的參數，並根據工作的接續使用型别 `task<T>`的參數。  如果擲回的工作有一個或多個數值繼續，那些繼續未排程執行。  下列範例會說明這項行為：  
  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 以工作為基礎的接續可讓您管理前項工作所擲回的任何例外狀況。  以工作為基礎的接續永遠執行；成功完成工作，是否擲回例外狀況，或已取消並不重要。  當工作擲回例外狀況時，會以工作的接續排定執行。  下列範例顯示必須擲回的工作。  工作有兩個繼續：一個以值為基礎，另一個以工作為基礎。  以工作為基礎的例外狀況一定會執行，也可能會攔截前項工作所擲回的例外狀況。  在這個範例指定兩個繼續完成時，會重新擲回例外狀況，因為工作例外狀況會擲回，在呼叫 `task::get` 或 `task::wait` 時。  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 建議您使用以工作為基礎的接續攔截的可以處理的例外狀況。  由於以工作為基礎的接續永遠執行，是否考慮將以工作的接續在接續鏈結結尾。  這有助於確保您的程式碼檢視所有例外狀況。  下列範例示範基本數值的接續鏈結。  鏈結中擲回的第三個工作，而且後面的任何數值繼續並未執行。  不過，最後的接續以工作為基礎，因此一定會執行。  這個最終繼續處理第三項工作所擲回的例外狀況。  
  
 我們建議您攔截可以最特定的例外狀況。  如果沒有攔截，特定的例外狀況可以省略這最後的以工作為基礎的接續。  所有例外狀況將會維持未處理且會結束應用程式。  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  您可以使用 [concurrency::task\_completion\_event::set\_exception](../../parallel/concrt/reference/task-completion-event-class.md) 方法來將例外狀況與工作完成事件。  [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 文件會進一步說明 [concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md) 類別。  
  
 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) 是與 `task`相關的重要執行階段例外狀況型別。  執行階段會擲回 `task_canceled` ，在呼叫 `task::get` 時，它會取消工作。\(相反地， `task::wait` 會傳回 [task\_status::canceled](../Topic/task_group_status%20Enumeration.md) ，而且不會擲回\)。您可以攔截和處理根據工作的接續之例外狀況，或當您呼叫 `task::get` 時。  如需工作取消的詳細資訊，請參閱[取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
> [!CAUTION]
>  不要擲回從程式碼的 `task_canceled` 。  呼叫 [concurrency::cancel\_current\_task](../Topic/cancel_current_task%20Function.md) 。  
  
 執行階段結束應用程式，如果工作擲回例外狀況，該例外狀況不是由工作、接續程式或主應用程式攔截。  如果您的應用程式損毀，您可以設定 Visual Studio 中斷，當 C\+\+ 例外狀況擲回時。  在您診斷未處理之例外狀況的位置之後，請使用以工作為基礎的接續處理它。  
  
 本文件的 [執行階段所擲回的例外狀況。](#runtime) 一節會說明如何將更詳細地與執行階段例外狀況一起使用。  
  
 \[[上方](#top)\]  
  
##  <a name="task_groups"></a> 工作群組和平行演算法  
 本節說明執行階段會如何處理工作群組所擲回的例外狀況。  本節也適用於 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 之類的平行演算法，因為這些演算法是建立在工作群組上。  
  
> [!CAUTION]
>  請確定您了解例外狀況對相依工作造成的影響。  如需如何的建議做法搭配工作或平行演算法的例外狀況處理，請查看在平行模式程式庫的主題中的最佳做法的 [了解取消和例外狀況處理對物件解構的影響](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) 區段。  
  
 如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 當您在傳遞給 [concurrency::task\_group](../Topic/task_group%20Class.md) 或 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件的工作函式的主體中擲回例外狀況時，執行階段會儲存該例外狀況，並將它封送處理至呼叫 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md)、[concurrency::structured\_task\_group::wait](../Topic/structured_task_group::wait%20Method.md)、[concurrency::task\_group::run\_and\_wait](../Topic/task_group::run_and_wait%20Method.md) 或 [concurrency::structured\_task\_group::run\_and\_wait](../Topic/structured_task_group::run_and_wait%20Method.md) 的內容。  執行階段也會停止工作群組中的所有作用中工作 \(包括子工作群組中的工作\)，並捨棄任何尚未啟動的工作。  
  
 下列範例顯示會擲回例外狀況之工作函式的基本結構。  此範例會使用 `task_group` 物件，以平行方式列印兩個 `point` 物件的值。  `print_point` 工作函式會將 `point` 物件的值列印至主控台。  如果輸入值是 `NULL`，則工作函式會擲回例外狀況。  執行階段會儲存這個例外狀況，並將它封送處理至呼叫 `task_group::wait` 的內容。  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 這個範例產生下列輸出。  
  
  **X \= 15, Y \= 30**  
**Caught exception: point is NULL.** 如需在工作群組中使用例外狀況處理的完整範例，請參閱 [如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="runtime"></a> 執行階段所擲回的例外狀況  
 例外狀況可能由執行階段呼叫。  大部分例外狀況類型，除了 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) 和 [concurrency::operation\_timed\_out](../../parallel/concrt/reference/operation-timed-out-class.md)，表示程式設計錯誤。  這些錯誤通常無法復原，因此不應該讓應用程式碼攔截或處理它們。  建議您只有在需要診斷程式設計錯誤時，才在應用程式程式碼中攔截或處理無法復原的錯誤。  不過，了解執行階段所定義的例外狀況型別，可協助您診斷程式設計錯誤。  
  
 執行階段所擲回的例外狀況，與工作函式所擲回的例外狀況，兩者使用的例外處理機制相同。  例如，[concurrency::receive](../Topic/receive%20Function.md) 函式會在未於指定的時間週期內收到訊息時，擲回 `operation_timed_out`。  如果 `receive` 在您傳遞給工作 \(Task\) 群組的工作 \(Work\) 函式中擲回例外狀況，則執行階段會儲存該例外狀況，並將它封送處理至呼叫 `task_group::wait`、`structured_task_group::wait`、`task_group::run_and_wait` 或 `structured_task_group::run_and_wait` 的內容。  
  
 下列範例會使用 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 演算法，以平行方式執行兩項工作。  第一項工作會先等候五秒，再將訊息傳送至訊息緩衝區。  第二項工作會使用 `receive` 函式，花三秒鐘的時間等候同一個訊息緩衝區送來訊息。  如果 `receive` 函式未在這個時間週期內收到訊息，則會擲回 `operation_timed_out`。  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 這個範例產生下列輸出。  
  
  **作業逾時。** 為了防止應用程式異常結束，請確定您的程式碼能夠處理執行階段發生的例外狀況。  另外也請處理使用並行執行階段的外部程式碼 \(例外協力廠商程式庫\) 所引發的例外狀況。  
  
 \[[上方](#top)\]  
  
##  <a name="multiple"></a> 多個例外狀況  
 如果工作或平行演算法收到多個例外狀況，則執行階段只會將其中一個例外狀況封送處理至呼叫端內容。  執行階段無法指出它一定會封送處理哪個例外狀況。  
  
 下列範例會使用 `parallel_for` 演算法，將數字列印至主控台。  如果輸入值小於某個最小值或是大於某個最大值，則會擲回例外狀況。  在這個範例中，可能有多個工作函式會擲回例外狀況。  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 下列顯示這個範例 \(Example\) 的範例 \(Sample\) 輸出。  
  
  **8**  
**2**  
**9**  
**3**  
**10**  
**4**  
**5**  
**6**  
**7**  
**Caught exception: \-5: the value is less than the minimum.** \[[上方](#top)\]  
  
##  <a name="cancellation"></a> 取消  
 並非所有的例外狀況都表示發生錯誤。  例如，搜尋演算法可能會在找到結果時，使用例外狀況處理來停止其相關聯的工作。  如需如何在程式碼中使用取消機制的詳細資訊，請參閱[取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="lwts"></a> 輕量型工作  
 輕量型工作是指您直接從 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 物件排定的工作。  輕量型工作帶來的負荷少於一般工作。  不過，執行階段並不會攔截輕量型工作所擲回的例外狀況。  這些例外狀況是由未處理例外處理常式來攔截，而這個處理常式預設會結束處理序。  因此，請在應用程式中使用適當的錯誤處理機制。  如需輕量型工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="agents"></a> 非同步代理程式  
 與對待輕量型工作的方式類似，執行階段並不會管理非同步代理程式所擲回的例外狀況。  
  
 下列範例顯示一個在衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的類別中處理例外狀況的方式。  這個範例會定義 `points_agent` 類別。  `points_agent::run` 方法會讀取訊息緩衝區中的 `point` 物件，並將這些物件列印至主控台。  `run` 方法會在收到 `NULL` 指標時擲回例外狀況。  
  
 `run` 方法會將所有工作都包在 `try`\-`catch` 區塊中。  `catch` 區塊會將例外狀況儲存在訊息緩衝區中。  應用程式會在代理程式完成之後讀取這個緩衝區，以檢查代理程式是否發生錯誤。  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 這個範例產生下列輸出。  
  
  **X: 10 Y: 20**  
**X: 20 Y: 30**  
**error occurred in agent: point must not be NULL**  
**the status of the agent is: done** 因為 `try`\-`catch` 區塊存在於 `while` 迴圈外部，所以代理程式會在發生第一個錯誤時結束處理。  如果 `try`\-`catch` 區塊是在 `while` 迴圈內部，則代理程式會在發生錯誤之後繼續進行。  
  
 這個範例會將例外狀況儲存在訊息緩衝區中，讓另一個元件可以在代理程式執行時監視代理程式遇到的錯誤。  這個範例會使用 [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) 物件來儲存錯誤。  在代理程式處理多個例外狀況的情況下，`single_assignment` 類別只會儲存傳遞給它的第一個訊息。  若只要儲存最後一個例外狀況，請使用 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 類別。  若要儲存所有例外狀況，請使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 類別。  如需這些訊息區塊的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 如需非同步代理程式的詳細資訊，請參閱[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="summary"></a> 摘要  
 \[[上方](#top)\]  
  
## 請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)