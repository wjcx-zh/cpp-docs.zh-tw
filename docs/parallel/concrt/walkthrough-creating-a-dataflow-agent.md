---
title: 逐步解說：建立資料流程代理程式
ms.date: 04/25/2019
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
ms.openlocfilehash: fa19d965a35909dfefc5f586c772bc9b4565e814
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142963"
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>逐步解說：建立資料流程代理程式

本檔示範如何建立以資料流程為基礎的以代理程式為基礎的應用程式，而不是控制流程。

*控制流程*指的是程式中作業的執行順序。 控制流程是使用控制結構（例如條件陳述式、迴圈等等）來進行管制。 或者，*資料流程*是指只有在所有必要的資料都可供使用時，才會進行計算的程式設計模型。 資料流程程式設計模型與「訊息傳遞」的概念有關，其中程式的獨立元件會藉由傳送訊息彼此通訊。

非同步代理程式同時支援控制流程和資料流程程式設計模型。 雖然控制流程模型適用于許多情況，但資料流程模型在其他情況下是適當的，例如，當代理程式接收資料，並根據該資料的承載執行動作時。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前，請先閱讀下列檔：

- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)

## <a name="top"></a> 章節

本逐步解說包含下列各節：

- [建立基本控制流程代理程式](#control-flow)

- [建立基本資料流程代理程式](#dataflow)

- [建立訊息記錄代理程式](#logging)

## <a name="control-flow"></a>建立基本控制流程代理程式

請考慮下列定義 `control_flow_agent` 類別的範例。 `control_flow_agent` 類別會在三個訊息緩衝區上運作：一個輸入緩衝區和兩個輸出緩衝區。 `run` 方法會從迴圈中的來源訊息緩衝區讀取，並使用條件陳述式來指示程式執行的流程。 代理程式會為非零的負值增加一個計數器，並為非零的正值增加另一個計數器。 在代理程式收到值為零的 sentinel 後，它會將計數器的值傳送至輸出訊息緩衝區。 `negatives` 和 `positives` 方法可讓應用程式讀取代理程式中的負值和正值的計數。

[!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]

雖然此範例會在代理程式中進行控制流程的基本使用，但它會示範以控制流程為基礎之程式設計的序列本質。 每個訊息都必須連續處理，即使輸入訊息緩衝區中可能有多個訊息可用也一樣。 資料流程模型可讓條件陳述式的兩個分支同時進行評估。 資料流程模型也可讓您建立更複雜的訊息網路，以在資料可供使用時對其採取動作。

[[靠上](#top)]

## <a name="dataflow"></a>建立基本資料流程代理程式

本節說明如何轉換 `control_flow_agent` 類別，以使用資料流程模型來執行相同的工作。

資料流程代理程式的運作方式是建立訊息緩衝區的網路，每一個都有特定的用途。 某些訊息區塊會使用篩選函式來依據其承載來接受或拒絕訊息。 篩選函數可確保訊息區塊只會接收特定的值。

#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>將控制流程代理程式轉換成資料流程代理程式

1. 將 `control_flow_agent` 類別的主體複製到另一個類別，例如 `dataflow_agent`。 或者，您也可以將 `control_flow_agent` 類別重新命名。

1. 移除從 `run` 方法呼叫 `receive` 之迴圈的主體。

[!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]

1. 在 `run` 方法中，`negative_count` 和 `positive_count`的變數初始化之後，加入 `countdown_event` 物件來追蹤使用中作業的計數。

[!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]

   本主題稍後會顯示 `countdown_event` 類別。

1. 建立將參與資料流程網路的訊息緩衝區物件。

[!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]

1. 連接訊息緩衝區以形成網路。

[!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]

1. 等候 `event` 並設定 `countdown event` 物件。 這些事件會通知代理程式已收到 sentinel 值，且所有作業都已完成。

[!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]

下圖顯示 `dataflow_agent` 類別的完整資料流程網路：

![資料流程網路](../../parallel/concrt/media/concrt_dataflow.png "資料流程網路")

下表描述網路的成員。

|成員|描述|
|------------|-----------------|
|`increment_active`|[Concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)物件，會遞增作用中的事件計數器，並將輸入值傳遞到網路的其餘部分。|
|`negatives`, `positives`|[concurrency：：呼叫](../../parallel/concrt/reference/call-class.md)遞增數位計數的物件，並遞減使用中的事件計數器。 每個物件都會使用篩選來接受負數或正數。|
|`sentinel`|[Concurrency：： call](../../parallel/concrt/reference/call-class.md)物件，只接受 sentinel 值零，並遞減作用中的事件計數器。|
|`connector`|將來源訊息緩衝區連接至內部網路的[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)物件。|

由於會在個別的執行緒上呼叫 `run` 方法，因此在網路完全連接之前，其他執行緒可以將訊息傳送至網路。 `_source` 資料成員是 `unbounded_buffer` 物件，可將從應用程式傳送的所有輸入緩衝至代理程式。 為確保網路處理所有輸入訊息，代理程式會先連結網路的內部節點，然後將該網路的啟動 `connector`連結到 `_source` 的資料成員。 這可確保在網路形成時，不會處理訊息。

因為此範例中的網路是以資料流程為基礎，而不是在控制流程上，所以網路必須與代理程式通訊，讓它完成每個輸入值的處理，而且 sentinel 節點已接收其值。 這個範例會使用 `countdown_event` 物件來表示已處理所有輸入值，而[concurrency：： event](../../parallel/concrt/reference/event-class.md)物件會指出 sentinel 節點已接收其值。 `countdown_event` 類別會使用 `event` 物件，以在計數器值達到零時發出信號。 資料流程網路的標頭會在每次收到值時遞增計數器。 網路的每個終端機節點會在處理輸入值之後，將計數器減一。 在代理程式形成資料流程網路之後，它會等候 sentinel 節點設定 `event` 物件，並針對 `countdown_event` 物件，通知其計數器已達到零。

下列範例會顯示 `control_flow_agent`、`dataflow_agent`和 `countdown_event` 類別。 `wmain` 函式會建立一個 `control_flow_agent` 和一個 `dataflow_agent` 物件，並使用 `send_values` 函數將一系列的隨機值傳送至代理程式。

[!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]

這個範例會產生下列範例輸出：

```Output
Control-flow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
Dataflow agent:
There are 500523 negative numbers.
There are 499477 positive numbers.
```

### <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `dataflow-agent.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

**cl/EHsc dataflow-agent .cpp**

[[靠上](#top)]

## <a name="logging"></a>建立訊息記錄代理程式

下列範例會顯示類似 `dataflow_agent` 類別的 `log_agent` 類別。 `log_agent` 類別會執行非同步記錄代理程式，以將記錄檔訊息寫入至檔案和主控台。 `log_agent` 類別可讓應用程式將訊息分類為資訊、警告或錯誤。 它也可讓應用程式指定每個記錄類別是否會寫入檔案、主控台或兩者。 這個範例會將所有記錄訊息寫入檔案，而且只會將錯誤訊息寫入主控台。

[!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]

這個範例會將下列輸出寫入主控台。

```Output
error: This is a sample error message.
```

這個範例也會產生包含下列文字的 log .txt 檔案。

```Output
info: ===Logging started.===
warning: This is a sample warning message.
error: This is a sample error message.
info: ===Logging finished.===
```

### <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `log-filter.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

**cl/EHsc log-filter .cpp**

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)
