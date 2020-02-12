---
title: 逐步解說：在啟用 COM 的應用程式中使用並行執行階段
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: faa072ab2b5973ace0f0ca138dcedffa56044213
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140630"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>逐步解說：在啟用 COM 的應用程式中使用並行執行階段

本檔示範如何在使用元件物件模型（COM）的應用程式中使用並行執行階段。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列檔：

- [工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [平行演算法](../../parallel/concrt/parallel-algorithms.md)

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

如需 COM 的詳細資訊，請參閱[元件物件模型（COM）](/windows/win32/com/component-object-model--com--portal)。

## <a name="managing-the-lifetime-of-the-com-library"></a>管理 COM 程式庫的存留期

雖然使用 COM 搭配並行執行階段遵循與任何其他並行機制相同的原則，但下列指導方針可協助您有效地使用這些程式庫。

- 執行緒必須先呼叫[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) ，才會使用 COM 程式庫。

- 執行緒可以多次呼叫 `CoInitializeEx`，只要它提供每個呼叫的相同引數即可。

- 對於 `CoInitializeEx`的每個呼叫，執行緒也必須呼叫[CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize)。 換句話說，`CoInitializeEx` 和 `CoUninitialize` 的呼叫必須平衡。

- 若要從某個執行緒單元切換至另一個執行緒，執行緒必須完全釋放 COM 程式庫，才能使用新的執行緒規格呼叫 `CoInitializeEx`。

當您使用 COM 搭配並行執行階段時，適用其他 COM 原則。 例如，在單一執行緒單元（STA）中建立物件，並將該物件封送處理至另一個公寓的應用程式，也必須提供訊息迴圈來處理傳入訊息。 也請記住，在公寓之間封送處理物件可能會降低效能。

### <a name="using-com-with-the-parallel-patterns-library"></a>使用 COM 搭配平行模式程式庫

當您使用 COM 搭配平行模式程式庫（PPL）中的元件（例如，工作組或平行演算法）時，請在每個工作或反復專案中使用 COM 程式庫之前呼叫 `CoInitializeEx`，並在每個工作或反復專案完成之前呼叫 `CoUninitialize`。 下列範例顯示如何使用[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件來管理 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

當工作或平行處理演算法取消或工作主體擲回例外狀況時，您必須確定 COM 程式庫已正確釋放。 若要確保工作在結束之前呼叫 `CoUninitialize`，請使用 `try-finally` 區塊或資源取得*為初始化*（RAII）模式。 下列範例會在工作完成或取消時，或擲回例外狀況時，使用 `try-finally` 區塊來釋放 COM 程式庫。

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

下列範例會使用 RAII 模式來定義 `CCoInitializer` 類別，以管理指定範圍內 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

您可以使用 `CCoInitializer` 類別，在工作結束時自動釋放 COM 程式庫，如下所示。

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

如需有關在並行執行階段中取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

### <a name="using-com-with-asynchronous-agents"></a>使用 COM 搭配非同步代理程式

當您使用 COM 搭配非同步代理程式時，請先呼叫 `CoInitializeEx`，然後再于代理程式的[concurrency：： agent：： run](reference/agent-class.md#run)方法中使用 com 程式庫。 然後在 `run` 方法傳回之前呼叫 `CoUninitialize`。 請勿在您的代理程式的函數或析構函式中使用 COM 管理常式，而且不會覆寫[concurrency：： agent：： start](reference/agent-class.md#start)或[concurrency：： agent：:d 一種](reference/agent-class.md#done)方法，因為這些方法是從不同的執行緒呼叫，而不是 `run` 方法。

下列範例顯示名為 `CCoAgent`的基本代理程式類別，它會管理 `run` 方法中的 COM 程式庫。

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

本逐步解說稍後會提供完整的範例。

### <a name="using-com-with-lightweight-tasks"></a>使用具有輕量工作的 COM

檔[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)描述並行執行階段中的輕量工作角色。 您可以使用 COM 搭配輕量工作，就像您在 Windows API 中傳遞給 `CreateThread` 函式的任何執行緒常式一樣。 這在下列範例中顯示。

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>啟用 COM 的應用程式範例

本節說明完整的啟用 COM 的應用程式，其使用 `IScriptControl` 介面來執行腳本，以計算<sup>第</sup>n 個斐的每個量值。 這個範例會先從主執行緒呼叫腳本，然後使用 PPL 和代理程式同時呼叫腳本。

請考慮下列 helper 函式，`RunScriptProcedure`，它會呼叫 `IScriptControl` 物件中的程式。

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain` 函式會建立 `IScriptControl` 物件，並在其中新增腳本來計算<sup>第</sup>n 個斐的量值，然後呼叫 `RunScriptProcedure` 函數來執行該腳本。

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>從 PPL 呼叫腳本

下列函式 `ParallelFibonacci`會使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法，以平行方式呼叫腳本。 此函式會在工作的每次反覆運算期間，使用 `CCoInitializer` 類別來管理 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

若要在範例中使用 `ParallelFibonacci` 函數，請在 `wmain` 函式傳回之前新增下列程式碼。

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>從代理程式呼叫腳本

下列範例會顯示 `FibonacciScriptAgent` 類別，它會呼叫腳本程式來計算<sup>第</sup>n 個斐的波納契數位。 `FibonacciScriptAgent` 類別會使用訊息傳遞，從主要程式接收到腳本函式的輸入值。 `run` 方法會管理整個工作中 COM 程式庫的存留期。

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

下列函式 `AgentFibonacci`會建立數個 `FibonacciScriptAgent` 物件，並使用訊息傳遞將數個輸入值傳送至這些物件。

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

若要在範例中使用 `AgentFibonacci` 函數，請在 `wmain` 函式傳回之前新增下列程式碼。

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>完整範例

下列程式碼顯示完整的範例，其使用平行演算法和非同步代理程式呼叫可計算斐數列數位的腳本程式。

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

此範例會產生下列範例輸出。

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

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `parallel-scripts.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc parallel-scripts .cpp/link ole32.lib .lib**

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
