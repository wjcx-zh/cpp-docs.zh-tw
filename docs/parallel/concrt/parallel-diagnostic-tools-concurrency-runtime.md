---
title: "平行診斷工具 （並行執行階段） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a7c6aa769faaacd128bb51a422227230fa4a851
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>平行診斷工具 (並行執行階段)
[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 可廣泛支援多執行緒應用程式的偵錯和分析。  
  
## <a name="debugging"></a>偵錯  
 Visual Studio 偵錯工具包括**平行堆疊**視窗中，**平行工作**視窗中，和**平行監看式**視窗。 如需詳細資訊，請參閱[逐步解說： 偵錯平行應用程式](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)和[How to： 使用平行監看式視窗](/visualstudio/debugger/how-to-use-the-parallel-watch-window)。  
  
## <a name="profiling"></a>程式碼剖析  
 程式碼剖析工具提供三種資料檢視會顯示圖形、 表格與數值多執行緒應用程式的互動方式與其本身和其他程式的相關資訊。 檢視可讓您快速識別的問題，區域，並以圖形方式顯示呼叫堆疊上的點從瀏覽呼叫 站台和原始程式碼。 如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。  
  
## <a name="event-tracing"></a>事件追蹤  
 並行執行階段會使用[Windows 事件追蹤](http://msdn.microsoft.com/library/windows/desktop/bb968803)(ETW) 各種事件發生時，通知檢測工具，分析工具，例如。 這些事件時，包含當排程器為啟用或停用、 在內容開始、 結束、 封鎖、 解除封鎖，或時，和平行演算法的開頭或結尾。  
  
 之類的工具[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)利用此功能; 因此，您通常不必直接使用這些事件。 不過，這些事件可在開發自訂的程式碼剖析工具，或當您使用事件追蹤工具例如[Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628)。  
  
 並行執行階段會引發這些事件只有在啟用追蹤時。 呼叫[concurrency:: enabletracing](reference/concurrency-namespace-functions.md#enabletracing)函式會啟用事件追蹤和[disabletracing](reference/concurrency-namespace-functions.md#disabletracing)函式來停用追蹤。  
  
 下表說明事件追蹤功能啟用時，執行階段引發的事件：  
  
|Event - 事件|描述|值|  
|-----------|-----------------|-----------|  

|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|並行執行階段的 ETW 提供者識別項。 |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|  
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|標記與內容相關的事件。 |`5727a00f-50be-4519-8256-f7699871fecb`|  
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|標示的進入和離開呼叫[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法。 |`31c8da6b-6165-4042-8b92-949e315f4d84`|  
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|標示的進入和離開呼叫[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法。 |`5cb7d785-9d66-465d-bae1-4611061b5434`|  
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|標示的進入和離開呼叫[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法。 |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|  
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|標記相關的事件[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|  
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|將標記與虛擬處理器相關的事件。 |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|  
  
 並行執行階段定義，但不目前引發，下列事件。 執行階段會保留供未來使用這些事件：  
  
-   [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)  
  
-   [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)  
  
-   [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)  
  
-   [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)  
  
-   [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)  
  
 [Concurrency:: concrt_eventtype](reference/concurrency-namespace-enums.md#concrt_eventtype)列舉型別指定追蹤事件的可能作業。 例如，在進入`parallel_for`演算法，執行階段引發`PPLParallelForEventGuid`事件，並提供`CONCRT_EVENT_START`的作業。 之前`parallel_for`演算法傳回，執行階段會再次引發`PPLParallelForEventGuid`事件，並提供`CONCRT_EVENT_END`的作業。  
  
 下列範例說明如何啟用追蹤呼叫`parallel_for`。 執行階段不追蹤的第一個呼叫`parallel_for`因為它未啟用追蹤。 若要呼叫`EnableTracing`讓執行階段追蹤的第二個呼叫`parallel_for`。  
  
 [!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]  
  
 執行階段追蹤，讓您呼叫次數`EnableTracing`和`DisableTracing`。 因此，如果您呼叫`EnableTracing`多次，您必須呼叫`DisableTracing`相同數目的時間才能停用追蹤。  
  
## <a name="see-also"></a>請參閱  
 [並行執行階段](../../parallel/concrt/concurrency-runtime.md)

