---
title: "並行執行階段的例外狀況處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72cde17c0bcb6a3582305167e6358f761c16f248
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>並行執行階段的例外狀況處理
並行執行階段使用 c + + 例外狀況處理來進行通訊的許多類型的錯誤。 這些錯誤包括在您提供給工作和工作群組的工作函式的使用無效的執行階段失敗，無法取得資源，例如執行階段錯誤，所發生的錯誤。 當工作或工作群組擲回例外狀況時，執行階段會保存該例外狀況，並將封送處理至等候工作或工作群組完成的內容。 例如輕量型工作和代理程式的元件，執行階段不會管理您的例外狀況。 在這些情況下，您必須實作自己的例外狀況處理機制。 本主題說明執行階段如何處理工作、 工作群組、 輕量型工作和非同步代理程式，所擲回的例外狀況，以及如何回應您的應用程式中的例外狀況。  
  
## <a name="key-points"></a>重點  
  
-   當工作或工作群組擲回例外狀況時，執行階段會保存該例外狀況，並將封送處理至等候工作或工作群組完成的內容。  
  
-   如果可能的話，括住每次呼叫[concurrency](reference/task-class.md#get)和[concurrency::task::wait](reference/task-class.md#wait)與`try` / `catch`區塊來處理，您可以復原的錯誤從。 如果工作擲回例外狀況和工作，其接續或主要的應用程式的其中一個未攔截到例外狀況，執行階段就會終止應用程式。  
  
-   以工作為基礎的接續一律會執行。並不重要是否順利完成，在前項工作擲回例外狀況，或已取消。 值為基礎的接續不會執行前項工作擲回或取消時。  
  
-   由於工作為基礎的接續一律會執行，請考慮是否要接續鏈結的結尾加入以工作為基礎的接續。 這可協助確保您的程式碼觀察到所有的例外狀況。  
  
-   執行階段會擲回[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)當您呼叫[concurrency](reference/task-class.md#get)並取消該工作。  

  
-   執行階段不會管理輕量型工作和代理程式例外的狀況。  
  
##  <a name="top"></a>本文件中  
  
- [工作和接續](#tasks)  
  
- [工作群組和平行演算法](#task_groups)  
  
- [執行階段擲回例外狀況](#runtime)  
  
- [多個例外狀況](#multiple)  
  
- [取消](#cancellation)  
  
- [輕量型工作](#lwts)  
  
- [非同步代理程式](#agents)  
  
##  <a name="tasks"></a>工作和接續  
 本章節描述執行階段如何處理所擲回的例外狀況[concurrency:: task](../../parallel/concrt/reference/task-class.md)物件和其接續工作。 如需工作和接續模型的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 當您擲回例外狀況傳遞至的工作函式主體中`task`物件，儲存該例外狀況，執行階段，並將其封送處理至呼叫的內容[concurrency](reference/task-class.md#get)或[concurrency::task:: wait](reference/task-class.md#wait)。 文件[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)描述與值為基礎的接續，但若要彙總，工作基礎值為基礎的接續會採用型別參數`T`和以工作為基礎的接續會採用一個參數類型`task<T>`. 如果工作擲回有一或多個值為基礎的接續，為了接續不會排程執行。 下列範例可說明此行為：  

  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 以工作為基礎的接續可讓您處理任何前項工作所擲回的例外狀況。 以工作為基礎的接續一律會執行。並不重要的工作已順利完成，發生例外狀況，或已取消。 當工作擲回例外狀況時，其以工作為基礎的接續會排定執行。 下列範例示範的工作，一律會擲回。 工作有兩個接續。其中一個是值為基礎，另一個方法是以工作為基礎。 以工作為基礎的例外狀況一定會執行，並可以攔截前項工作所擲回的例外狀況。 此範例會等候這兩個接續來完成，會擲回例外狀況再次因為工作一律擲回例外狀況時`task::get`或`task::wait`呼叫。  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 我們建議您使用以工作為基礎的接續攔截能夠處理的例外狀況。 由於工作為基礎的接續一律會執行，請考慮是否要接續鏈結的結尾加入以工作為基礎的接續。 這可協助確保您的程式碼觀察到所有的例外狀況。 下列範例示範基本的值為基礎的接續鏈結。 鏈結中的第三個工作擲回，並因此不會執行任何值為基礎的接續在它後面。 不過，最後的接續是以工作為基礎，因此一定會執行。 這個最後的接續會處理第三個工作所擲回的例外狀況。  
  
 我們建議您攔截您可以最適合的例外狀況。 如果您沒有來攔截特定例外狀況，您可以省略這個最後一個以工作為基礎的接續。 任何例外狀況會保留未處理，而且可以結束應用程式。  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  您可以使用[concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md)例外狀況關聯工作完成事件的方法。 文件[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)描述[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)更詳細的類別。  
  

 [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)是與相關的重要的執行階段例外狀況類型`task`。 執行階段會擲回`task_canceled`當您呼叫`task::get`並取消該工作。 (相反地，`task::wait`傳回[task_status:: canceled](reference/concurrency-namespace-enums.md#task_group_status)並不會擲回。)您可以攔截並處理這個例外狀況，從以工作為基礎的接續，或當您呼叫`task::get`。 如需工作取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。  

  
> [!CAUTION]
>  永遠不會從您的程式碼擲回 `task_canceled`。 呼叫[concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)改為。  
  
 如果工作擲回例外狀況和工作，其接續或主要的應用程式的其中一個未攔截到例外狀況，執行階段就會終止應用程式。 如果您的應用程式當機，您可以設定 Visual Studio c + + 例外狀況時中斷。 診斷的未處理的例外狀況的位置之後，使用以工作為基礎的接續來處理它。  
  
 區段[由執行階段擲回的例外狀況](#runtime)本文件說明如何在更詳細的執行階段例外狀況。  
  
 [[靠上](#top)]  
  
##  <a name="task_groups"></a>工作群組和平行演算法  

 本章節描述執行階段如何處理工作群組所擲回的例外狀況。 本章節也適用於平行演算法例如[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，因為這些演算法建置在工作群組上。  
  
> [!CAUTION]
>  請確定您了解例外狀況都有相依的工作的效果。 如需有關如何使用例外狀況處理的工作或平行演算法的建議作法，請參閱[了解如何取消和例外狀況處理物件解構的影響](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)> 一節中以平行方式的最佳作法模式程式庫的主題。  
  
 如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  

 當您擲回例外狀況傳遞至的工作函式主體中[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件，儲存該例外狀況，執行階段，並將其封送處理若要呼叫的內容[task_group](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [run_and_wait](reference/task-group-class.md#run_and_wait)，或[run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 執行階段也會停止所有作用中工作 （包括子工作群組中） 的工作群組中，並會捨棄任何尚未開始的工作。  

  
 下列範例會擲回例外狀況的工作函式的基本結構。 此範例會使用`task_group`列印兩個值的物件`point`平行中的物件。 `print_point`工作函式會列印值`point`物件至主控台。 工作函式擲回例外狀況，如果輸入的值為`NULL`。 儲存此例外狀況，執行階段，並將其封送處理至呼叫的內容`task_group::wait`。  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
X = 15, Y = 30Caught exception: point is NULL.  
```  
  
 如需使用例外狀況處理在工作群組中的完整範例，請參閱[How to： 使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。  
  
 [[靠上](#top)]  
  
##  <a name="runtime"></a>執行階段擲回例外狀況  
 例外狀況可能起因於執行階段呼叫。 大部分的例外狀況類型，除了[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)和[concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md)，會指出程式設計錯誤。 這些錯誤通常是無法復原，並因此不應該攔截或處理應用程式碼。 我們建議您只攔截或無法復原的錯誤處理應用程式程式碼中，如果您要診斷的程式設計錯誤。 不過，了解例外狀況類型所定義的執行階段可協助您診斷的程式設計錯誤。  
  
 例外狀況處理機制是相同的執行階段為工作函式所擲回的例外狀況擲回的例外狀況。 例如， [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式會擲回`operation_timed_out`當它未收到一則訊息中指定的時間週期。 如果`receive`工作函式中擲回例外狀況，您傳遞給工作群組，執行階段會儲存該例外狀況，並將封送處理至呼叫的內容`task_group::wait`， `structured_task_group::wait`， `task_group::run_and_wait`，或`structured_task_group::run_and_wait`。  
  
 下列範例會使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法以平行方式執行兩項工作。 第一項工作會等候 5 秒，然後將訊息傳送至訊息緩衝區。 第二個工作使用`receive`等待三秒鐘的時間從相同的訊息緩衝區中接收訊息的函式。 `receive`函式會擲回`operation_timed_out`如果沒有收到訊息的時間週期中。  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
The operation timed out.  
```  
  
 若要防止應用程式異常終止，請確定您的程式碼在執行階段會呼叫時，會處理例外狀況。 當您呼叫外部程式碼會使用並行執行階段中，例如，協力廠商程式庫時，也可以處理的例外狀況。  
  
 [[靠上](#top)]  
  
##  <a name="multiple"></a>多個例外狀況  
 如果工作或平行演算法收到多個例外狀況，執行階段封送處理這些例外狀況至呼叫的內容的其中之一。 執行階段不保證它將封送處理的例外狀況。  
  
 下列範例會使用`parallel_for`列印到主控台的數字的演算法。 它會擲回例外狀況，如果輸入的值小於某些最小值或大於某些最大值。 在此範例中，多個工作函式會擲回例外狀況。  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 下圖顯示此範例的範例輸出。  
  
```Output  
8293104567Caught exception: -5: the value is less than the minimum.  
```  
  
 [[靠上](#top)]  
  
##  <a name="cancellation"></a>取消  
 並非所有的例外狀況表示發生錯誤。 比方說，搜尋演算法可能會停止其相關聯的工作，在找到結果時使用例外狀況處理。 如需如何在您的程式碼中使用取消機制的詳細資訊，請參閱[PPL 中的取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
 [[靠上](#top)]  
  
##  <a name="lwts"></a>輕量型工作  
 輕量型工作是直接從排程的工作[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)物件。 輕量型工作會執行較少的額外負荷比一般工作。 不過，執行階段不會攔截輕量型工作所擲回的例外狀況。 相反地，未處理例外狀況處理常式，其預設值終止處理序會攔截到例外狀況。 因此，應用程式中使用適當的錯誤處理機制。 如需輕量型工作的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 [[靠上](#top)]  
  
##  <a name="agents"></a>非同步代理程式  
 輕量型工作，例如執行階段不會管理非同步代理程式所擲回的例外狀況。  
  
 下列範例示範衍生自的類別中處理例外狀況的一種方法[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 這個範例會定義`points_agent`類別。 `points_agent::run`方法會讀取`point`物件自訊息緩衝區，並將其列印至主控台。 `run`方法擲回例外狀況，如果收到`NULL`指標。  
  
 `run`方法周圍中的所有工作`try` - `catch`區塊。 `catch`區塊訊息緩衝區中儲存的例外狀況。 應用程式會檢查是否的代理程式遇到錯誤藉由這個緩衝區讀取代理程式完成之後。  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
X: 10 Y: 20  
X: 20 Y: 30  
error occurred in agent: point must not be NULL  
the status of the agent is: done  
```  
  
 因為`try` - `catch`區塊存在於外部`while`迴圈，代理程式就會結束處理作業時遇到的第一個錯誤。 如果`try` - `catch`區塊已內`while`迴圈，代理程式會繼續之後發生錯誤。  
  
 此範例訊息緩衝區中儲存例外狀況，以便在其執行另一個元件可以監視的代理程式的錯誤。 這個範例會使用[concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md)儲存錯誤物件。 在代理程式處理多個的例外狀況的地方的情況下`single_assignment`類別會儲存只有第一個訊息傳遞給它。 若要儲存的最後一個例外狀況，使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別。 若要儲存的所有例外狀況，使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)類別。 如需這些訊息區塊的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 如需非同步代理程式的詳細資訊，請參閱[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)。  
  
 [[靠上](#top)]  
  
##  <a name="summary"></a> 總結  
 [[靠上](#top)]  
  
## <a name="see-also"></a>請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

