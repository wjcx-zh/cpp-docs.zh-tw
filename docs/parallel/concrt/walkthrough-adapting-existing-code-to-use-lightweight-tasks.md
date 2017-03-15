---
title: "逐步解說：改寫現有程式碼以使用輕量型工作 | Microsoft Docs"
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
  - "使用輕量型工作 [並行執行階段]"
  - "輕量型工作，使用 [並行執行階段]"
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 逐步解說：改寫現有程式碼以使用輕量型工作
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何將使用 Windows API 來建立和執行執行緒的現有程式碼，改寫為使用輕量型工作。  
  
 「*輕量型工作*」是指您直接從 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 或 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 物件排定的工作。  當您改寫現有程式碼以使用並行執行階段的排程功能時，輕量型工作非常有用。  
  
## 必要條件  
 在開始這個逐步解說之前，請先閱讀[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md) 主題。  
  
## 範例  
  
### 說明  
 下列範例說明使用 Windows API 來建立和執行執行緒的一般用法。  這個範例會使用 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 函式在個別的執行緒上呼叫 `MyThreadFunction`。  
  
### 程式碼  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### 註解  
 這個範例產生下列輸出。  
  
  **Parameters \= 50, 100** 下列步驟顯示如何改寫這個程式碼範例以使用並行執行階段來執行相同的工作。  
  
### 若要改寫這個範例以使用輕量型工作  
  
1.  加入標頭檔 concrt.h 的 `#include` 指示詞。  
  
     [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  加入 `concurrency` 命名空間的 `using` 指示詞。  
  
     [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  將 `MyThreadFunction` 的宣告變更為使用 `__cdecl` 呼叫慣例並傳回 `void`。  
  
     [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  修改 `MyData` 結構以包含 [concurrency::event](../../parallel/concrt/reference/event-class.md) 物件，這個物件會對主應用程式發出工作已完成的信號。  
  
     [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  以 [concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md) 方法呼叫取代 `CreateThread` 方法呼叫。  
  
     [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  
6.  以 [concurrency::event::wait](../Topic/event::wait%20Method.md) 方法呼叫取代 `WaitForSingleObject` 方法呼叫，以等候工作完成。  
  
     [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  移除 `CloseHandle` 呼叫。  
  
8.  變更 `MyThreadFunction` 之定義的簽章，以符合步驟 3。  
  
     [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. 在 `MyThreadFunction` 函式的結尾，呼叫 [concurrency::event::set](../Topic/event::set%20Method.md) 方法以對主應用程式發出工作已完成的信號。  
  
     [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. 從 `MyThreadFunction` 中移除 `return` 陳述式。  
  
## 範例  
  
### 說明  
 下列已完成的範例顯示使用輕量型工作來呼叫 `MyThreadFunction` 函式的程式碼。  
  
### 程式碼  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### 註解  
  
## 請參閱  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler 類別](../../parallel/concrt/reference/scheduler-class.md)