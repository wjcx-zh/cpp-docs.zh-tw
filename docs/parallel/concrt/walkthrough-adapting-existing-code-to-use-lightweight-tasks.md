---
title: 逐步解說：改寫現有程式碼以使用輕量型工作
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: e7c6096829a1cd45cfdb849a1899d6b4a2d4cb78
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142000"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>逐步解說：改寫現有程式碼以使用輕量型工作

本主題說明如何調整使用 Windows API 的現有程式碼，以建立和執行執行緒以使用輕量工作。

*輕量*工作是您直接從[concurrency：：](../../parallel/concrt/reference/scheduler-class.md) schedule 或[concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)物件排程的工作。 輕量型工作適用於當您調整現有程式碼以使用並行執行階段的排程功能時。

## <a name="prerequisites"></a>必要條件

開始本逐步解說之前，請先閱讀[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)的主題。

## <a name="example"></a>範例

下列範例說明 Windows API 的一般使用方式，以建立和執行執行緒。 這個範例會使用[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函數，在不同的執行緒上呼叫 `MyThreadFunction`。

### <a name="initial-code"></a>初始程式碼

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

此範例會產生下列輸出。

```Output
Parameters = 50, 100
```

下列步驟示範如何調整程式碼範例，以使用並行執行階段來執行相同的工作。

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>若要調整範例以使用輕量工作

1. 新增 concrt 標頭檔的 `#include` 指示詞。

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. 加入 `concurrency` 命名空間的 `using` 指示詞。

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. 將 `MyThreadFunction` 的宣告變更為使用 `__cdecl` 呼叫慣例，並傳回 `void`。

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. 修改 `MyData` 結構以包含[concurrency：： event](../../parallel/concrt/reference/event-class.md)物件，以向主應用程式發出工作已完成的信號。

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. 以[concurrency：： CurrentScheduler：： ScheduleTask](reference/currentscheduler-class.md#scheduletask)方法的呼叫取代 `CreateThread` 的呼叫。

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. 以[concurrency：： event：： wait](reference/event-class.md#wait)方法的呼叫取代 `WaitForSingleObject` 的呼叫，以等候工作完成。

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. 移除 `CloseHandle`的呼叫。

1. 將 `MyThreadFunction` 定義的簽章變更為符合步驟3。

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. 在 `MyThreadFunction` 函式的結尾，呼叫[concurrency：： event：： set](reference/event-class.md#set)方法，以對主應用程式發出工作已完成的信號。

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. 從 `MyThreadFunction`移除 `return` 語句。

### <a name="completed-code"></a>完成的程式碼

下列已完成的範例顯示使用輕量工作呼叫 `MyThreadFunction` 函式的程式碼。

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler 類別](../../parallel/concrt/reference/scheduler-class.md)
