---
title: 如何：建立在延遲之後才會完成的工作
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 89564a00dbfde078ef98cd53110853e30e33ad6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616264"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>如何：建立在延遲之後才會完成的工作

此範例示範如何使用[concurrency:: task](../../parallel/concrt/reference/task-class.md)， [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)， [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)， [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)， [concurrency:: timer](../../parallel/concrt/reference/timer-class.md)，以及[concurrency:: call](../../parallel/concrt/reference/call-class.md)類別來建立在延遲之後完成的工作。 您可以使用這個方法建立執行下列動作的迴圈：偶爾輪詢資料，引入逾時，延遲使用者輸入處理長達一段預先定義的時間等等。

## <a name="example"></a>範例

下列範例顯示 `complete_after` 和 `cancel_after_timeout` 函式。 `complete_after` 函式會建立在指定的延遲之後完成的 `task` 物件。 它會使用 `timer` 物件和 `call` 物件將 `task_completion_event` 物件設定在指定的延遲之後。 您可以使用 `task_completion_event` 類別定義在執行緒或另一個工作表示有可用值之後完成的工作。 設定事件之後，接聽程式的工作便會完成，而且其後續工作會排定繼續執行。

> [!TIP]
>  如需詳細資訊`timer`並`call`類別，也就是非同步代理程式程式庫的一部分，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

如果工作未在指定的逾時之前完成，`cancel_after_timeout` 函式就會在 `complete_after` 函式上建置以取消該工作。 `cancel_after_timeout` 函式會建立兩個工作。 第一個工作會指出成功，並且在提供的工作完成後完成，第二個工作會指出失敗，並且在指定的逾時後完成。 `cancel_after_timeout` 函式會建立在成功或失敗的工作完成後執行的接續工作。 如果失敗的工作先完成，則接續工作會取消語彙基元來源以取消整個工作。

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>範例

下列範例會多次計算範圍 [0, 100000] 中質數的計數。 如果作業未在特定時間限制內完成，則會失敗。 `count_primes` 函式將示範如何使用 `cancel_after_timeout` 函式。 它會計算某一特定範圍中質數的數目，而如果工作未在提供的時間內完成，則會失敗。 `wmain` 函式會多次呼叫 `count_primes` 函式。 每次它都會將時間限制減半。 若作業未在目前時間限制內完成，程式就會結束。

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

如果您使用這個技巧在延遲之後取消工作，在取消整個工作之後，任何尚未開始的工作都不會開始。 然而重要的是，任何長時間執行的工作都要及時回應取消作業。 如需有關工作取消的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

## <a name="example"></a>範例

以下是這個範例的完整程式碼：

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

若要編譯程式碼，將它複製然後將它貼在 Visual Studio 專案中，或將它貼在檔案，稱為`task-delay.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc task-delay.cpp**

## <a name="see-also"></a>另請參閱

[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task 類別 (並行執行階段)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token 類別](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event 類別](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer 類別](../../parallel/concrt/reference/timer-class.md)<br/>
[call 類別](../../parallel/concrt/reference/call-class.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)

