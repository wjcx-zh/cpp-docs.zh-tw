---
title: "逐步解說：建立資料流程代理程式 | Microsoft Docs"
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
  - "建立資料流程代理程式 [並行執行階段]"
  - "資料流程代理程式，建立 [並行執行階段]"
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 逐步解說：建立資料流程代理程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明如何建立以資料流程 \(而不是控制流程\) 為基礎的代理程式架構應用程式。  
  
 「*控制流程*」\(Control Flow\) 是指程式中作業執行的順序。  控制流程是透過條件陳述式、迴圈等控制結構來規範。  另一方面，「*資料流程*」\(Dataflow\) 是指只在所有必要資料皆可用的情況下執行計算的程式撰寫模型。  資料流程程式撰寫模型與訊息傳遞的概念有關，在此模型中，程式的獨立元件可藉由訊息傳送相互通訊。  
  
 非同步代理程式支援控制流程和資料流程程式撰寫模型。  雖然控制流程模型適合許多情況，但在某些情況下，資料流程模型更適用，例如當代理程式接收資料並根據該資料的裝載來執行動作時。  
  
## 必要條件  
 在您開始閱讀此逐步解說前，請先參閱下列文件：  
  
-   [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
##  <a name="top"></a> 章節  
 此逐步解說包含下列章節：  
  
-   [建立基本的控制流程代理程式](#control-flow)  
  
-   [建立基本的資料流程代理程式](#dataflow)  
  
-   [建立訊息記錄代理程式](#logging)  
  
##  <a name="control-flow"></a> 建立基本的控制流程代理程式  
 請考慮下列會定義 `control_flow_agent` 類別的範例。  `control_flow_agent` 類別作用於三個訊息緩衝區：一個輸入緩衝區和兩個輸出緩衝區。  `run` 方法會在迴圈中從來源訊息緩衝區讀取，並使用條件陳述式來導向程式執行流程。  如果是非零的負值，代理程式會遞增一個計數值，如果是非零的正值，則會遞增另一個計數器。  在代理程式收到零的 Sentinel 值之後，它會將計數器的值傳送至輸出訊息緩衝區。  `negatives` 和 `positives` 方法可讓應用程式從代理程式讀取負值和正值的計數。  
  
 [!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_1.cpp)]  
  
 雖然這個範例在代理程式中使用控制流程的基本用法，但是它示範控制流程架構程式設計的序列本質。  每則訊息都必須循序處理，即使在輸入訊息緩衝區中有多個訊息也一樣。  資料流程模型可讓條件陳述式的分支同時評估。  資料流程模型也可讓您建立更複雜的訊息網路，在資料可用時作用於資料。  
  
 \[[上方](#top)\]  
  
##  <a name="dataflow"></a> 建立基本的資料流程代理程式  
 本節說明如何將 `control_flow_agent` 類別轉換為使用資料流程模型，執行相同的工作。  
  
 資料流程代理程式的運作方式是建立訊息緩衝區網路，每個訊息緩衝區都會做為特定用途。  某些訊息區塊使用篩選函式，根據訊息裝載來接受或拒絕訊息。  篩選函式可確保訊息區塊只接收特定值。  
  
#### 若要將控制流程代理程式轉換為資料流程代理程式  
  
1.  將 `control_flow_agent` 類別的主體複製到另一個類別，例如 `dataflow_agent`。  或者，您可以重新命名 `control_flow_agent` 類別。  
  
2.  從 `run` 方法中移除會呼叫 `receive` 的迴圈主體。  
  
     [!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_2.cpp)]  
  
3.  在 `run` 方法中，於變數 `negative_count` 和 `positive_count` 的初始化之後，加入 `countdown_event` 物件，追蹤使用中作業的計數。  
  
     [!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_3.cpp)]  
  
     本主題稍後會說明 `countdown_event` 類別。  
  
4.  建立會參與資料流程網路的訊息緩衝區物件。  
  
     [!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_4.cpp)]  
  
5.  連接訊息緩衝區以形成網路。  
  
     [!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_5.cpp)]  
  
6.  等候 `event` 和 `countdown event` 物件設定。  這些事件表示代理程式已收到 Sentinel 值，而且所有作業都已完成。  
  
     [!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_6.cpp)]  
  
 下圖顯示 `dataflow_agent` 類別的完整資料流程網路：  
  
 ![資料流程網路](../../parallel/concrt/media/concrt_dataflow.png "ConcRT\_Dataflow")  
  
 下表說明網路成員。  
  
|成員|說明|  
|--------|--------|  
|`increment_active`|[concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) 物件，會遞增使用中事件計數器，並將輸入值傳遞給網路的其餘部分。|  
|`negatives`, `positives`|[concurrency::call](../../parallel/concrt/reference/call-class.md) 物件，會遞增數字計數，並遞減使用中事件計數器。  每個這些物件都會使用篩選條件以接受負數或正數。|  
|`sentinel`|[concurrency::call](../../parallel/concrt/reference/call-class.md) 物件，只會接受零的 Sentinel 值，並遞減使用中事件計數器。|  
|`connector`|[concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 物件，會將來源訊息緩衝區連接至內部網路。|  
  
 因為 `run` 方法是在個別執行緒上呼叫的，所以其他執行緒可以在網路完全連接之前傳送訊息給網路。  `_source` 資料成員是 `unbounded_buffer` 物件，會緩衝從應用程式傳送至代理程式的所有輸入。  為了確定網路處理所有輸入訊息，代理程式會先連結網路的內部節點，然後將該網路前端 \(`connector`\) 連結至 `_source` 資料成員。  這會確保不會在網路形成過程中處理訊息。  
  
 因為在這個範例中網路是以資料流程 \(而不是控制流程\) 為基礎，網路必須向代理程式表示它已完成處理每個輸入值，以及 Sentinel 節點已收到其值。  這個範例使用 `countdown_event` 物件以表示所有輸入值都已處理，使用 [concurrency::event](../../parallel/concrt/reference/event-class.md) 物件以表示 Sentinel 節點收到其值。  `countdown_event` 類別使用 `event` 物件，在計數器值達到零時發出訊號。  每次資料流程網路前端收到值時，它會遞增計數器。  網路的每個終端節點在處理輸入值之後，它會遞減計數器。  在代理程式形成資料流程網路之後，它會等候 Sentinel 節點設定 `event` 物件，以及等候 `countdown_event` 物件表示其計數器已達到零。  
  
 下列範例顯示 `control_flow_agent`、`dataflow_agent` 和 `countdown_event` 類別。  `wmain` 函式會建立 `control_flow_agent` 和 `dataflow_agent` 物件，並使用 `send_values` 函式將一系列的隨機值傳送給代理程式。  
  
 [!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_7.cpp)]  
  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出：  
  
  **控制流程代理程式:**  
**有 500523 個負數。**  
**有 499477 個正數。**  
**資料流程代理程式:**  
**有 500523 個負數。**  
**有 499477 個正數。**   
### 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `dataflow-agent.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc dataflow\-agent.cpp**  
  
 \[[上方](#top)\]  
  
##  <a name="logging"></a> 建立訊息記錄代理程式  
 下列範例顯示 `log_agent` 類別，這個類別與 `dataflow_agent` 類別類似。  `log_agent` 類別實作非同步記錄代理程式，會將記錄訊息寫入檔案和主控台。  `log_agent` 類別可讓應用程式將訊息分類為資訊、警告或錯誤。  它也會讓應用程式指定每個記錄分類要寫入檔案、主控台或兩者。  這個範例會將所有記錄訊息寫入檔案，而且只將錯誤訊息寫入主控台。  
  
 [!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-dataflow-agent_8.cpp)]  
  
 這個範例會將下列輸出寫入主控台。  
  
  **錯誤:這是範例錯誤訊息。** 這個範例也會產生 log.txt 檔案，包含下列文字。  
  
  **詳細資訊: \=\=\= 開始登入 \=\=\=**  
**警告: 這是個範例警告訊息。**  
**錯誤: 這是個範例錯誤訊息。**  
**詳細資訊: \=\=\= 登入結束 \=\=\=**   
### 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `log-filter.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc log\-filter.cpp**  
  
 \[[上方](#top)\]  
  
## 請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)