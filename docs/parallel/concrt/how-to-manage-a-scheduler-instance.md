---
title: "如何：管理排程器執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "管理排程器執行個體 [並行執行階段]"
  - "排程器執行個體, 管理 [並行執行階段]"
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：管理排程器執行個體
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

排程器執行個體可讓您為特定的排程原則與不同種類的工作負載建立關聯。  本主題包含兩個基本範例，這些範例顯示如何建立和管理排程器執行個體。  
  
 這些範例建立的排程器會使用預設排程器原則。  如需建立使用自訂原則之排程器的範例，請參閱 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
### 若要管理應用程式中的排程器執行個體  
  
1.  建立 [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) 物件，這個物件包含要供排程器使用的原則值。  
  
2.  呼叫 [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) 方法或 [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) 方法，以建立排程器執行個體。  
  
     如果您使用 `Scheduler::Create` 方法，則當您需要將排程器與目前內容產生關聯時，請呼叫 [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) 方法。  
  
3.  呼叫 [CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) 函式，為未發出信號、自動重設的事件物件建立控制代碼。  
  
4.  將您剛才建立之事件物件的控制代碼傳遞給 [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) 方法或 [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md) 方法。  這會在排程器被終結時註冊此事件。  
  
5.  執行您想要目前排程器排定的工作。  
  
6.  呼叫 [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) 方法，中斷目前排程器的連結並且還原先前的排程器做為目前的排程器。  
  
     如果您使用 `Scheduler::Create` 方法，請呼叫 [concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) 方法將 `Scheduler` 物件的參考計數遞減。  
  
7.  將事件的控制代碼傳遞給 [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) 函式，以等候排程器關閉。  
  
8.  呼叫 [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) 函式關閉事件物件的控制代碼。  
  
## 範例  
 下列程式碼顯示兩種管理排程器執行個體的方法。  每個範例都會先使用預設排程器來執行將目前排程器的唯一識別項列印出來的工作。  然後，每個範例都會使用某個排程器執行個體再次執行相同的工作。  最後，每個範例都會還原預設排程器做為目前的排程器，然後再執行一次工作。  
  
 第一個範例會使用 [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) 類別來建立排程器執行個體，並將它與目前的內容建立關聯。  第二個範例會使用 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 類別來執行相同的工作。  通常，`CurrentScheduler` 類別用於使用目前的排程器。  當您要控制何時將排程器與目前的內容產生關聯，或當您要將特定排程器與特定工作產生關聯時，第二個範例 \(這個範例使用 `Scheduler` 類別\) 會很有用。  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/CPP/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **Using CurrentScheduler class...**  
**Current scheduler id: 0**  
**Creating and attaching scheduler...**  
**Current scheduler id: 1**  
**Detaching scheduler...**  
**Current scheduler id: 0**  
**Using Scheduler class...**  
**Current scheduler id: 0**  
**Creating scheduler...**  
**Attaching scheduler...**  
**Current scheduler id: 2**  
**Detaching scheduler...**  
**Current scheduler id: 0**   
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `scheduler-instance.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc scheduler\-instance.cpp**  
  
## 請參閱  
 [排程器執行個體](../../parallel/concrt/scheduler-instances.md)   
 [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)