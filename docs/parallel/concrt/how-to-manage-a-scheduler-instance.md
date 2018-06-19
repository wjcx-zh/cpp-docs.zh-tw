---
title: 如何： 管理排程器執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 699abcbc75dc4f0df40d07d26c0e6987d4711fe3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687656"
---
# <a name="how-to-manage-a-scheduler-instance"></a>如何：管理排程器執行個體
排程器執行個體，可讓您將特定的排程原則與各種類型的工作負載產生關聯。 本主題包含兩個基本範例示範如何建立及管理排程器執行個體。  
  
 範例會建立使用預設排程器原則的排程器。 如需建立排程器的範例使用自訂原則，請參閱[How to： 指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
### <a name="to-manage-a-scheduler-instance-in-your-application"></a>若要管理您的應用程式中的排程器執行個體  
  
1.  建立[schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)排程器使用的物件，其中包含原則值。  
  

2.  呼叫[concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create)方法或[scheduler](reference/scheduler-class.md#create)方法，以建立排程器執行個體。  
  
     如果您使用`Scheduler::Create`方法，請呼叫[concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)方法，當您需要將排程器與目前的內容產生關聯。  
  
3.  呼叫[CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396)函式來建立事件未收到訊號，自動重設物件的控制代碼。  
  
4.  將控制代碼傳遞至您剛才建立的事件物件[concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)方法或[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)方法。 如此會註冊排程器時，也要設定的事件。  
  
5.  執行您想要排程的目前排程器工作。  
  
6.  呼叫[concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach)卸離目前的排程器和還原先前的排程器與目前的方法。  
  
     如果您使用`Scheduler::Create`方法，請呼叫[concurrency::Scheduler::Release](reference/scheduler-class.md#release)方法的參考計數遞減`Scheduler`物件。  
  
7.  將控制代碼傳遞至事件，以[WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032)等候關閉排程器的函式。  
  
8.  呼叫[CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211)函式來關閉事件物件的控制代碼。  
  
## <a name="example"></a>範例  
 下列程式碼會示範兩種方式管理排程器執行個體。 每個範例一開始會使用預設排程器執行的工作會列印出目前的排程器的唯一識別碼。 每個範例接著會使用排程器執行個體重新執行相同的工作。 最後，每個範例會還原為目前的預設排程器，並執行工作一次。  
  
 第一個範例會使用[concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)建立排程器執行個體，並將它與目前內容關聯的類別。 第二個範例會使用[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)類別以執行相同的工作。 一般而言，`CurrentScheduler`類別用來處理目前的排程器。 第二個範例使用`Scheduler`類別中，當您想要控制排程器與目前內容相關聯時，或當您想要將特定排程器與特定工作產生關聯時非常有用。  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
Using CurrentScheduler class...  
 
Current scheduler id: 0  
Creating and attaching scheduler...  
Current scheduler id: 1  
Detaching scheduler...  
Current scheduler id: 0  
 
Using Scheduler class...  
 
Current scheduler id: 0  
Creating scheduler...  
Attaching scheduler...  
Current scheduler id: 2  
Detaching scheduler...  
Current scheduler id: 0  
```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`scheduler-instance.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 排程器 instance.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [排程器執行個體](../../parallel/concrt/scheduler-instances.md)   
 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

