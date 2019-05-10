---
title: 逐步解說：在啟用 COM 的應用程式中使用並行執行階段
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 7249dc1c715861230170bc3efd4fb4aa75029bdb
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857504"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>逐步解說：在啟用 COM 的應用程式中使用並行執行階段

本文件將示範如何使用並行執行階段中使用元件物件模型 (COM) 的應用程式。

## <a name="prerequisites"></a>必要條件

在開始本逐步解說之前，請閱讀下列文件：

- [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [平行演算法](../../parallel/concrt/parallel-algorithms.md)

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

如需有關 COM 的詳細資訊，請參閱[元件物件模型 (COM)](/windows/desktop/com/component-object-model--com--portal)。

## <a name="managing-the-lifetime-of-the-com-library"></a>管理 COM 程式庫的存留期

雖然使用 COM 與並行執行階段會遵循相同的原則，做為任何其他並行機制，下列指導方針可協助您有效地一起使用這些程式庫。

- 必須在呼叫執行緒[CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex)它會使用 COM 程式庫之前。

- 執行緒可以呼叫`CoInitializeEx`多次，只要它會提供每個呼叫的相同引數。

- 每次呼叫`CoInitializeEx`，還必須呼叫執行緒[CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize)。 換句話說，呼叫`CoInitializeEx`和`CoUninitialize`必須達成平衡。

- 若要從單一執行緒 apartment 中，切換到另一個，執行緒必須完全釋放 COM 程式庫之前它會呼叫`CoInitializeEx`與新執行緒規格。

當您將 COM 使用並行執行階段時，就會適用其他 COM 原則。 例如，在單一執行緒 apartment (STA) 中建立的物件，並封送處理至另一個 apartment，該物件的應用程式也必須提供處理內送訊息的訊息迴圈。 也請記住封送處理物件 apartment 之間可能會降低效能。

### <a name="using-com-with-the-parallel-patterns-library"></a>使用平行模式程式庫中的 COM

當您使用的 COM 元件在平行模式程式庫 (PPL)，例如工作群組或平行演算法，與呼叫`CoInitializeEx`每個工作或反覆項目，並呼叫期間使用的 COM 程式庫之前`CoUninitialize`每個工作或反覆項目完成之前. 下列範例示範如何管理與 COM 程式庫的存留期[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件。

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

您必須確定取消工作或平行演算法時，或工作主體擲回例外狀況時，就會正確地釋放 COM 程式庫。 若要保證，工作會呼叫`CoUninitialize`結束之前，請使用`try-finally`區塊或*資源擷取即初始化*(RAII) 模式。 下列範例會使用`try-finally`區塊來釋放 COM 程式庫，當工作完成或已取消，或擲回例外狀況時。

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

下列範例會使用 RAII 模式來定義`CCoInitializer`類別，用來管理在給定範圍中的 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

您可以使用`CCoInitializer`，如下所示的工作結束時，會自動釋放 COM 程式庫的類別。

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

如需並行執行階段中的取消作業的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

### <a name="using-com-with-asynchronous-agents"></a>使用非同步代理程式的 COM

當您使用非同步代理程式使用 COM 時，呼叫`CoInitializeEx`才能使用中的 COM 程式庫[2&gt;concurrency::agent::run&lt;2}](reference/agent-class.md#run)代理程式的方法。 然後呼叫`CoUninitialize`之前`run`方法會傳回。 不使用 COM 管理常式中的建構函式或解構函式的代理程式，並不會覆寫[concurrency::agent::start](reference/agent-class.md#start)或是[concurrency:: agent:: 完成](reference/agent-class.md#done)方法因為這些方法從以外的執行緒呼叫`run`方法。

下列範例示範基本的代理程式類別，名為`CCoAgent`，其可管理中的 COM 程式庫`run`方法。

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

本逐步解說稍後會提供完整的範例。

### <a name="using-com-with-lightweight-tasks"></a>COM 使用輕量型工作

文件[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)說明並行執行階段的輕量型工作的角色。 您可以使用 COM 使用輕量型工作，就如同您傳遞至任何執行緒常式與`CreateThread`Windows API 中的函式。 這在下列範例中顯示。

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>啟用 COM 的應用程式範例

此區段會顯示完整啟用 COM 使用的應用程式`IScriptControl`介面，以執行指令碼，會計算 n<sup>th</sup> Fibonacci 數字。 此範例會從主執行緒中，會先呼叫指令碼，並接著會使用 PPL 和代理程式同時呼叫指令碼。

請考慮下列 helper 函式`RunScriptProcedure`，它會在呼叫程序`IScriptControl`物件。

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain`函式會建立`IScriptControl`物件，將指令碼的程式碼加入至它計算 n<sup>th</sup> Fibonacci 數字，然後再呼叫`RunScriptProcedure`函式來執行該指令碼。

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>從 PPL 呼叫指令碼

下列函式中， `ParallelFibonacci`，使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法以平行方式呼叫指令碼。 此函式會使用`CCoInitializer`類別來管理工作的每個反覆項目期間的 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

若要使用`ParallelFibonacci`函式的範例中，新增下列程式碼，再`wmain`函式會傳回。

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>呼叫指令碼，從代理程式

下列範例所示`FibonacciScriptAgent`類別，呼叫的指令碼程序，來計算 n<sup>th</sup> Fibonacci 數字。 `FibonacciScriptAgent`類別會使用訊息傳遞至接收，從主程式中，輸入指令碼函式的值。 `run`方法會管理的 COM 程式庫，在整個工作存留期。

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

下列函式中， `AgentFibonacci`，建立數個`FibonacciScriptAgent`物件，並使用訊息傳遞至傳送數個輸入值，這些物件。

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

若要使用`AgentFibonacci`函式的範例中，新增下列程式碼，再`wmain`函式會傳回。

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>完整範例

下列程式碼顯示完整的範例中，會使用平行演算法和非同步代理程式來呼叫計算 Fibonacci 數字的指令碼程序。

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

此範例會產生下列輸出範例。

```Output
Main Thread:
fib(15) = 610

Parallel Fibonacci:
fib(15) = 610
fib(10) = 55
fib(16) = 987
fib(18) = 2584
fib(11) = 89
fib(17) = 1597
fib(19) = 4181
fib(12) = 144
fib(13) = 233
fib(14) = 377

Agent Fibonacci:
fib(30) = 832040
fib(22) = 17711
fib(10) = 55
fib(12) = 144
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`parallel-scripts.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 平行 scripts.cpp /link ole32.lib**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
