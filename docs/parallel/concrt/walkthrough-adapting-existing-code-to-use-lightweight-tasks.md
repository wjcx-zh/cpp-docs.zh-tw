---
title: 逐步解說： 改寫現有程式碼以使用輕量型工作 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fe3bb4b576bd1f9160b4a3cdc3142be5cdff05
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>逐步解說：改寫現有程式碼以使用輕量型工作
本主題說明如何調整現有程式碼使用 Windows API 來建立和執行使用輕量型工作的執行緒。  
  
 A*輕量型工作*是直接從排程的工作[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)或[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)物件。 輕量型工作適用於當您調整現有程式碼以使用並行執行階段的排程功能時。  
  
## <a name="prerequisites"></a>必要條件  
 在開始這個逐步解說之前，請閱讀本主題[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例將說明 Windows API 來建立和執行執行緒的一般使用方式。 這個範例會使用[CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453)函式呼叫`MyThreadFunction`另一個執行緒上。  
  
### <a name="code"></a>程式碼  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### <a name="comments"></a>註解  
 此範例會產生下列輸出。  
  
```Output  
Parameters = 50, 100  
```  
  
 下列步驟顯示如何調整程式碼範例以使用並行執行階段來執行相同的工作。  
  
### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>若要調整範例以使用輕量型工作  
  
1.  新增`#include`標頭檔 concrt.h 指示詞。  
  
 [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  新增`using`指示詞`concurrency`命名空間。  
  
 [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  變更宣告`MyThreadFunction`使用`__cdecl`呼叫慣例，並傳回`void`。  
  
 [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  修改`MyData`結構以包含[concurrency:: event](../../parallel/concrt/reference/event-class.md)對主應用程式發出工作已完成的物件。  
  
 [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  呼叫取代`CreateThread`呼叫[concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask)方法。  

  
 [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  

6.  呼叫取代`WaitForSingleObject`呼叫[concurrency::event::wait](reference/event-class.md#wait)方法等候工作完成。  

 [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  移除呼叫`CloseHandle`。  
  
8.  變更定義的簽章`MyThreadFunction`以符合步驟 3。  
  
 [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. 在結尾`MyThreadFunction`函式，呼叫[concurrency::event::set](reference/event-class.md#set)方法來通知主應用程式發出工作已完成。  
  
 [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. 移除`return`陳述式從`MyThreadFunction`。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 已完成下列範例顯示使用輕量型工作來呼叫的程式碼`MyThreadFunction`函式。  
  
### <a name="code"></a>程式碼  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### <a name="comments"></a>註解  
  
## <a name="see-also"></a>另請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler 類別](../../parallel/concrt/reference/scheduler-class.md)
