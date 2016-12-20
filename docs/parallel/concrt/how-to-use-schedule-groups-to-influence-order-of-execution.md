---
title: "如何：使用排程群組來影響執行順序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "排程群組，使用 [並行執行階段]"
  - "使用排程群組 [並行執行階段]"
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用排程群組來影響執行順序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在並行執行階段中，工作的排定順序並不是絕對的。  不過，您可以使用排程原則來影響執行工作的順序。  本主題顯示如何搭配使用排程群組與 [concurrency::SchedulingProtocol](../Topic/PolicyElementKey%20Enumeration.md) 排程器原則，以影響工作的執行順序。  
  
 這個範例會執行同一組工作兩次，每次都使用不同的排程原則。  這兩個原則都會將處理資源數目上限限制為 2。  第一次執行會使用 `EnhanceScheduleGroupLocality` 原則 \(預設值\)，而第二次執行則會使用 `EnhanceForwardProgress` 原則。  在 `EnhanceScheduleGroupLocality` 原則下，排程器會執行一個排程群組中的所有工作，直到完成或產生每個工作為止。  在 `EnhanceForwardProgress` 原則下，排程器會在完成或產生一個工作之後，立即使用循環配置資源方式移至下一個排程群組。  
  
 將 `EnhanceScheduleGroupLocality` 原則用在排程群組時，因為每個排程群組都包含相關聯的工作，而這個原則會保留工作之間的快取位置，因此效能會得到改善。  `EnhanceForwardProgress` 原則則可讓工作往前進行，當您需要公平排定所有排程群組時，這個原則會很有用。  
  
## 範例  
 這個範例定義衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的 `work_yield_agent` 類別。  `work_yield_agent` 類別會執行一個單位的工作、產生目前的內容，然後執行另一個單位的工作。  代理程式會使用 [concurrency::wait](../Topic/wait%20Function.md) 函式以合作方式讓渡目前的內容，讓其他內容可以執行。  
  
 這個範例會建立四個 `work_yield_agent` 物件。  為了說明如何設定排程器原則以影響代理程式的執行順序，這個範例會將前兩個代理程式與某個排程群組相關聯，並將後兩個代理程式與另一個排程群組相關聯。  這個範例會使用 [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) 方法建立 [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) 物件。  這個範例會執行這四個代理程式兩次，每次都使用不同的排程原則。  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/CPP/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **使用 EnhanceScheduleGroupLocality…**  
**群組 0，工作 0:第一個迴圈…**  
**群組 0，工作 1:第一個迴圈…**  
**群組 0，工作 0:等候…**  
**群組 1，工作 0:第一個迴圈…**  
**群組 0，工作 1:等候…**  
**群組 1，工作 1:第一個迴圈…**  
**群組 1，工作 0:等候…**  
**群組 0，工作 0:第二個迴圈…**  
**群組 1，工作 1:等候…**  
**群組 0，工作 1:第二個迴圈…**  
**群組 0，工作 0:完成…**  
**群組 1，工作 0:第二個迴圈…**  
**群組 0，工作 1:完成…**  
**群組 1，工作 1:第二個迴圈…**  
**群組 1，工作 0:完成…**  
**群組 1，工作 1:完成…**  
**使用 EnhanceForwardProgress…**  
**群組 0，工作 0:第一個迴圈…**  
**群組 1，工作 0:第一個迴圈…**  
**群組 0，工作 0:等候…**  
**群組 0，工作 1:第一個迴圈…**  
**群組 1，工作 0:等候…**  
**群組 1，工作 1:第一個迴圈…**  
**群組 0，工作 1:等候…**  
**群組 0，工作 0:第二個迴圈…**  
**群組 1，工作 1:等候…**  
**群組 1，工作 0:第二個迴圈…**  
**群組 0，工作 0:完成…**  
**群組 0，工作 1:第二個迴圈…**  
**群組 1，工作 0:完成…**  
**群組 1，工作 1:第二個迴圈…**  
**群組 0，工作 1:完成…**  
**群組 1，工作 1:完成…** 這兩個原則都會產生相同的事件序列。  不過，使用 `EnhanceScheduleGroupLocality` 的原則會先啟動屬於第一個排程群組的兩個代理程式，再啟動屬於第二個群組的代理程式。  使用 `EnhanceForwardProgress` 的原則會啟動第一個群組中的某個代理程式，然後再啟動第二個群組中的第一個代理程式。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `scheduling-protocol.cpp`  的檔案中，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe \/EHsc scheduling\-protocol.cpp**  
  
## 請參閱  
 [排程群組](../../parallel/concrt/schedule-groups.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)