---
title: "輕量型工作 | Microsoft Docs"
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
  - "輕量型工作"
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 輕量型工作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明輕量型工作在並行執行階段中的角色。  「*輕量型工作*」\(Lightweight Task\) 是指您直接從 `concurrency::Scheduler` 或 `concurrency::ScheduleGroup` 物件排程的工作。  輕量型工作類似於您提供給 Windows API [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式的函式。  因此，當您改編現有程式碼以使用並行執行階段的排程功能時，輕量型工作非常有用。  並行執行階段本身會使用輕量型工作來排程非同步代理程式，並在非同步訊息區之間傳送訊息。  
  
> [!TIP]
>  並行執行階段提供了預設排程器，因此您不需要在應用程式中建立排程器。  因為工作排程器有助於微調應用程式效能，如果您是並行執行階段的新使用者，建議請從[平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)開始。  
  
 輕量型工作的額外負荷低於非同步代理程式和工作群組。  例如，執行階段並不會在輕量型工作完成時對您發出通知。  此外，執行階段也不會攔截或處理輕量型工作所擲回的例外狀況。  如需例外狀況處理和輕量型工作的詳細資訊，請參閱[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 對於大部分的工作，我們建議您使用更強大的功能，例如工作群組與平行演算法，因為它們可讓您更易於將複雜的工作簡化成基本工作。  如需工作群組的詳細資訊，請參閱[工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  如需平行演算法的詳細資訊，請參閱[平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 若要建立輕量型工作，請呼叫 [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md)、[concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md) 或 [concurrency::Scheduler::ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md) 方法。  若要等候輕量型工作完成，請靜待父排程器關閉，或使用同步處理機制，例如 [concurrency::event](../../parallel/concrt/reference/event-class.md) 物件。  
  
## 範例  
 如需相關範例，以便了解如何改編現有程式碼以使用輕量型工作，請參閱[逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)。  
  
## 請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [逐步解說：改寫現有程式碼以使用輕量型工作](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)