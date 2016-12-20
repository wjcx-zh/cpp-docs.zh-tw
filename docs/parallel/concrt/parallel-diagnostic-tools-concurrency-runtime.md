---
title: "平行診斷工具 (並行執行階段) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "平行診斷工具 [並行執行階段]"
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
caps.latest.revision: 15
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 平行診斷工具 (並行執行階段)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 可更廣泛地支援多執行緒應用程式的偵錯和分析。  
  
## 偵錯  
 Visual Studio 偵錯工具包括 \[**平行堆疊**\] 視窗、 \[**平行工作**\] 視窗和 \[**平行監看式**\] 視窗。  如需詳細資訊，請參閱[逐步解說：偵錯平行應用程式](../Topic/Walkthrough:%20Debugging%20a%20Parallel%20Application.md)與[如何：使用平行監看式視窗](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md)。  
  
## 程式碼剖析  
 程式碼剖析工具提供了三種資料檢視，可透過圖形、表格與數值的形式，顯示多執行緒應用程式如何與其本身和其他程式互動的相關資訊。  這些檢視可讓您快速找出您所需的區域，以及從圖形顯示上的點巡覽至呼叫堆疊、呼叫位置與原始程式碼。  如需詳細資訊，請參閱[並行視覺化檢視](../Topic/Concurrency%20Visualizer.md)。  
  
## 事件追蹤  
 並行執行階段使用 [Windows 事件追蹤](http://msdn.microsoft.com/library/windows/desktop/bb968803) \(ETW\)，在發生各種事件時通知檢測工具，例如分析工具。  這些事件包含當排程器啟動或停用時，當內容開始、結束、封鎖、解除封鎖或讓渡時，以及當平行演算法開始或結束時。  
  
 [並行視覺化檢視](../Topic/Concurrency%20Visualizer.md)等工具會利用此功能，因此，您通常不必直接使用這些事件。  不過，當您開發自訂分析工具，或使用 [Xperf](http://go.microsoft.com/fwlink/?LinkID=160628) \(英文\) 等事件追蹤工具時，這些事件很實用。  
  
 並行執行階段只在啟用追蹤時引發這些事件。  呼叫 [concurrency::EnableTracing](../Topic/EnableTracing%20Function.md) 函式啟用事件追蹤，呼叫 [concurrency::DisableTracing](../Topic/DisableTracing%20Function.md) 函式停用事件追蹤。  
  
 下表說明啟用事件追蹤時執行階段引發的事件：  
  
|事件|說明|值|  
|--------|--------|-------|  
|[concurrency::ConcRT\_ProviderGuid](../Topic/ConcRT_ProviderGuid%20Constant.md)|並行執行階段的 ETW 提供者識別碼。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[concurrency::ContextEventGuid](../Topic/ContextEventGuid%20Constant.md)|標記與內容相關的事件。|`5727a00f-50be-4519-8256-f7699871fecb`|  
|[concurrency::PPLParallelForEventGuid](../Topic/PPLParallelForEventGuid%20Constant.md)|標記 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法呼叫的進入和離開。|`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[concurrency::PPLParallelForeachEventGuid](../Topic/PPLParallelForeachEventGuid%20Constant.md)|標記 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 演算法呼叫的進入和離開。|`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[concurrency::PPLParallelInvokeEventGuid](../Topic/PPLParallelInvokeEventGuid%20Constant.md)|標記 [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) 演算法呼叫的進入和離開。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[concurrency::SchedulerEventGuid](../Topic/SchedulerEventGuid%20Constant.md)|標記與[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)相關的事件。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[concurrency::VirtualProcessorEventGuid](../Topic/VirtualProcessorEventGuid%20Constant.md)|標記與虛擬處理器相關的事件。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 並行執行階段定義了 \(但目前不引發\) 下列事件。  執行階段保留這些事件供未來使用：  
  
-   [concurrency::ConcRTEventGuid](../Topic/ConcRTEventGuid%20Constant.md)  
  
-   [concurrency::ScheduleGroupEventGuid](../Topic/SchedulerEventGuid%20Constant.md)  
  
-   [concurrency::ChoreEventGuid](../Topic/ChoreEventGuid%20Constant.md)  
  
-   [concurrency::LockEventGuid](../Topic/LockEventGuid%20Constant.md)  
  
-   [concurrency::ResourceManagerEventGuid](../Topic/ResourceManagerEventGuid%20Constant.md)  
  
 [concurrency::ConcRT\_EventType](../Topic/ConcRT_EventType%20Enumeration.md) 列舉指定事件追蹤的可能作業。  例如，在進入 `parallel_for` 演算法時，執行階段會引發 `PPLParallelForEventGuid` 事件並提供 `CONCRT_EVENT_START` 做為作業。  在 `parallel_for` 演算法傳回之前，執行階段會再次引發 `PPLParallelForEventGuid` 事件並提供 `CONCRT_EVENT_END` 做為作業。  
  
 下列範例會說明如何針對 `parallel_for` 的呼叫啟用追蹤。  執行階段不會追蹤 `parallel_for` 的第一個呼叫，因為未啟用追蹤。  呼叫 `EnableTracing` 可讓執行階段追蹤 `parallel_for` 的第二個呼叫。  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/CPP/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 執行階段會追蹤您呼叫 `EnableTracing` 和 `DisableTracing` 的次數。  因此，如果您呼叫 `EnableTracing` 多次，則必須呼叫相同次數的 `DisableTracing`，以便停用追蹤。  
  
## 請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)