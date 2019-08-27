---
title: 輕量型工作
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 7b798312c9660e51338d51a97a052ad4e5bdca6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512174"
---
# <a name="lightweight-tasks"></a>輕量型工作

本檔說明並行執行階段中輕量工作的角色。 *輕量*工作是您直接從`concurrency::Scheduler`或`concurrency::ScheduleGroup`物件排程的工作。 輕量工作與您提供給 Windows API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函數的函式類似。 因此, 當您調整現有的程式碼以使用並行執行階段的排程功能時, 輕量工作會很有用。 並行執行階段本身會使用輕量工作來排程非同步代理程式, 並在非同步訊息區塊之間傳送訊息。

> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能, 因此如果您不熟悉並行執行階段, 建議您從[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫開始。

輕量工作的額外負荷低於非同步代理程式和工作組。 例如, 執行時間不會在輕量工作完成時通知您。 此外, 執行時間不會攔截或處理從輕量工作擲回的例外狀況。 如需例外狀況處理和輕量工作的詳細資訊, 請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

對於大部分的工作, 我們建議您使用更健全的功能, 例如工作組和平行演算法, 因為它們可讓您更輕鬆地將複雜的工作分解成更基本的工作。 如需工作組的詳細資訊, 請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。 如需平行演算法的詳細資訊, 請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。

若要建立輕量工作, 請呼叫[concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask)、 [Concurrency:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)或[concurrency:: 排程器:: ScheduleTask](reference/scheduler-class.md#scheduletask)方法。 若要等候輕量工作完成, 請等候父排程器關閉, 或使用同步處理機制, 例如[concurrency:: event](../../parallel/concrt/reference/event-class.md)物件。

## <a name="example"></a>範例

如需示範如何調整現有程式碼以使用輕量工作的範例, 請[參閱逐步解說:調整現有程式碼以使用輕](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)量工作。

## <a name="see-also"></a>另請參閱

[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
