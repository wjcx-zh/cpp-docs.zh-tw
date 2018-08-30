---
title: 輕量型工作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8548412436be6e505c0ea08a2991e6948496f592
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210280"
---
# <a name="lightweight-tasks"></a>輕量型工作
本文件說明並行執行階段的輕量型工作的角色。 A*輕量型工作*是直接從排程的工作`concurrency::Scheduler`或`concurrency::ScheduleGroup`物件。 輕量型工作類似您提供給 Windows API 函式[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)函式。 因此，輕量工作會很有用，當您調整現有的程式碼，以使用並行執行階段的排程功能時。 並行執行階段本身會使用輕量型工作，來排程非同步代理程式和傳送非同步訊息區塊之間的訊息。  
  
> [!TIP]
>  並行執行階段會提供預設排程器，因此您不需要在應用程式中建立排程器。 由於工作排程器可協助您微調應用程式的效能，建議您先使用[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)如果您是新並行執行階段。  
  
 輕量型工作會執行較少的額外負荷比非同步代理程式和工作群組。 例如，執行階段並不會通知您輕量型工作完成時。 此外，執行階段不會攔截或處理從輕量型工作擲回的例外狀況。 如需有關例外狀況處理和輕量型工作的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 對於大部分的工作，我們建議使用更強固的功能，例如工作群組，和平行演算法因為它們可讓您更輕鬆地分成複雜的工作更基本的項目。 如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。 如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 若要建立輕量型工作，請呼叫[concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask)， [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask)，或[concurrency::Scheduler::ScheduleTask](reference/scheduler-class.md#scheduletask)方法。 若要等候輕量型工作完成時，等候 父排程器關閉，或使用同步處理機制，例如[concurrency:: event](../../parallel/concrt/reference/event-class.md)物件。  
  
## <a name="example"></a>範例  
 如需示範如何調整現有的程式碼，以使用輕量型工作的範例，請參閱 <<c0> [ 逐步解說： 改寫現有程式碼加入以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

