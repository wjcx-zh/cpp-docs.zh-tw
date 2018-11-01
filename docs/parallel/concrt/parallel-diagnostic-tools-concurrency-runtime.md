---
title: 平行診斷工具 (並行執行階段)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 44bb32f87379a05829816234ee8bc412de1f24b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608568"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>平行診斷工具 (並行執行階段)

Visual Studio 可廣泛支援多執行緒應用程式的偵錯與分析。

## <a name="debugging"></a>偵錯

Visual Studio 偵錯工具包含**平行堆疊** 視窗中，**平行工作**視窗中，並**平行監看式**視窗。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 偵錯平行應用程式](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)並[如何： 使用平行監看式視窗](/visualstudio/debugger/how-to-use-the-parallel-watch-window)。

## <a name="profiling"></a>程式碼剖析

程式碼剖析工具提供三個資料檢視，它會顯示圖形、 表格與數值資訊與其本身和其他程式，多執行緒應用程式的互動方式。 檢視可讓您快速識別需要關注的並以圖形方式顯示呼叫堆疊上的點從瀏覽呼叫站台和原始程式碼。 如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。

## <a name="event-tracing"></a>事件追蹤

並行執行階段會使用[的 Windows 事件追蹤](/windows/desktop/ETW/event-tracing-portal)(ETW) 的各種事件發生時通知檢測工具，分析工具，例如。 這些事件包括啟用或停用排程器時、 當內容開始、 結束、 封鎖、 解除封鎖，或產生，以及當平行演算法的開頭或結尾。

之類的工具[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)利用這項功能; 因此，您通常不必直接使用這些事件。 不過，這些事件可讓開發自訂的分析工具時，或當您使用事件追蹤工具這類[Xperf](http://go.microsoft.com/fwlink/p/?linkid=160628)。

並行執行階段會引發這些事件，只有當啟用追蹤時。 呼叫[concurrency:: enabletracing](reference/concurrency-namespace-functions.md#enabletracing)函式來啟用事件追蹤並[disabletracing](reference/concurrency-namespace-functions.md#disabletracing)函式來停用追蹤。

下表描述當啟用事件追蹤時，執行階段會引發的事件：

|Event - 事件|描述|值|
|-----------|-----------------|-----------|

|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|並行執行階段的 ETW 提供者識別項。 |`f7b697a3-4db5-4d3b-be71-c4d284e6592f`| |[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|將標記與內容相關的事件。 |`5727a00f-50be-4519-8256-f7699871fecb`| |[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|進入和離開的呼叫會將標示[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法。 |`31c8da6b-6165-4042-8b92-949e315f4d84`| |[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|進入和離開的呼叫會將標示[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法。 |`5cb7d785-9d66-465d-bae1-4611061b5434`| |[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|進入和離開的呼叫會將標示[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法。 |`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`| |[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|將標記事件的相關[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 |`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`| |[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|將標記與虛擬處理器相關的事件。 |`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

並行執行階段定義，但不會目前引發，下列事件。 Runtime 會保留供日後使用這些事件：

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: concrt_eventtype](reference/concurrency-namespace-enums.md#concrt_eventtype)列舉會指定可能的事件追蹤的作業。 例如，在進入`parallel_for`演算法，執行階段會引發`PPLParallelForEventGuid`事件，並提供`CONCRT_EVENT_START`的作業。 再`parallel_for`演算法傳回時，會再次引發執行階段`PPLParallelForEventGuid`事件，並提供`CONCRT_EVENT_END`的作業。

下列範例說明如何啟用追蹤的呼叫`parallel_for`。 執行階段不追蹤的第一個呼叫`parallel_for`因為追蹤不會啟用它。 若要在呼叫`EnableTracing`可讓執行階段追蹤的第二個呼叫`parallel_for`。

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

執行階段會追蹤您所呼叫的次數`EnableTracing`和`DisableTracing`。 因此，如果您呼叫`EnableTracing`多次，您必須呼叫`DisableTracing`相同數目的時間才能停用追蹤。

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)

