---
title: 平行診斷工具 (並行執行階段)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Diagnostic Tools [Concurrency Runtime]
ms.assetid: b1a3f1d2-f5df-4f29-852e-906b3d8341fc
ms.openlocfilehash: 34b2421dfc53deeb35dcc659a8d555983e583737
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510506"
---
# <a name="parallel-diagnostic-tools-concurrency-runtime"></a>平行診斷工具 (並行執行階段)

Visual Studio 可廣泛支援多執行緒應用程式的偵錯與分析。

## <a name="debugging"></a>偵錯

Visual Studio 偵錯工具包括 [**平行堆疊**] 視窗、[**平行**工作] 視窗和 [**平行監看**式] 視窗。 如需詳細資訊，請參閱[逐步解說：調試平行應用程式](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)和[如何:使用 [平行監看](/visualstudio/debugger/how-to-use-the-parallel-watch-window)式] 視窗。

## <a name="profiling"></a>程式碼剖析

程式碼剖析工具提供三種資料檢視, 顯示多執行緒應用程式如何與本身和其他程式互動的圖形化、表格式和數值資訊。 這些視圖可讓您快速找出問題的範圍, 並從圖形化顯示器上的點導覽至呼叫堆疊、呼叫網站和原始程式碼。 如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。

## <a name="event-tracing"></a>事件追蹤

並行執行階段會使用[Windows 事件追蹤](/windows/win32/ETW/event-tracing-portal)(ETW), 在發生各種事件時通知偵查工具 (例如分析工具)。 這些事件包括排程器何時啟動或停用、內容開始、結束、封鎖、解除封鎖或產生, 以及平行演算法開始或結束的時間。

[並行視覺化](/visualstudio/profiling/concurrency-visualizer)之類的工具會利用這種功能;因此, 您通常不需要直接使用這些事件。 不過, 當您開發自訂 profiler 或使用事件追蹤工具 (例如[Xperf](https://go.microsoft.com/fwlink/p/?linkid=160628)) 時, 這些事件會很有用。

只有在啟用追蹤時, 並行執行階段才會引發這些事件。 呼叫[concurrency:: EnableTracing](reference/concurrency-namespace-functions.md#enabletracing)函數以啟用事件追蹤, 並使用[Concurrency::D isabletracing](reference/concurrency-namespace-functions.md#disabletracing)函式來停用追蹤。

下表描述啟用事件追蹤時, 執行時間引發的事件:

|Event - 事件|描述|值|
|-----------|-----------------|-----------|
|[concurrency::ConcRT_ProviderGuid](reference/concurrency-namespace-constants1.md#concrt_providerguid)|並行執行階段的 ETW 提供者識別碼。|`f7b697a3-4db5-4d3b-be71-c4d284e6592f`|
|[concurrency::ContextEventGuid](reference/concurrency-namespace-constants1.md#contexteventguid)|標示與內容相關的事件。|`5727a00f-50be-4519-8256-f7699871fecb`|
|[concurrency::PPLParallelForEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeventguid)|將進入和結束標記為對[concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法的呼叫。|`31c8da6b-6165-4042-8b92-949e315f4d84`|
|[concurrency::PPLParallelForeachEventGuid](reference/concurrency-namespace-constants1.md#pplparallelforeacheventguid)|將進入和結束標記為對[concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法的呼叫。|`5cb7d785-9d66-465d-bae1-4611061b5434`|
|[concurrency::PPLParallelInvokeEventGuid](reference/concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|將進入和結束標記為對[concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法的呼叫。|`d1b5b133-ec3d-49f4-98a3-464d1a9e4682`|
|[concurrency::SchedulerEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)|標示與[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)相關的事件。|`e2091f8a-1e0a-4731-84a2-0dd57c8a5261`|
|[concurrency::VirtualProcessorEventGuid](reference/concurrency-namespace-constants1.md#virtualprocessoreventguid)|標示與虛擬處理器相關的事件。|`2f27805f-1676-4ecc-96fa-7eb09d44302f`|

並行執行階段定義 (但目前不會引發) 下列事件。 執行時間會保留這些事件以供日後使用:

- [concurrency::ConcRTEventGuid](reference/concurrency-namespace-constants1.md#concrteventguid)

- [concurrency::ScheduleGroupEventGuid](reference/concurrency-namespace-constants1.md#schedulereventguid)

- [concurrency::ChoreEventGuid](reference/concurrency-namespace-constants1.md#choreeventguid)

- [concurrency::LockEventGuid](reference/concurrency-namespace-constants1.md#lockeventguid)

- [concurrency::ResourceManagerEventGuid](reference/concurrency-namespace-constants1.md#resourcemanagereventguid)

[Concurrency:: ConcRT_EventType](reference/concurrency-namespace-enums.md#concrt_eventtype)列舉會指定事件追蹤的可能作業。 例如, 在`parallel_for`演算法的進入處, 執行時間會`PPLParallelForEventGuid`引發事件, 並提供`CONCRT_EVENT_START`做為作業。 在演算法傳回之前, 執行時間會再次`PPLParallelForEventGuid`引發事件, 並`CONCRT_EVENT_END`提供做為作業。 `parallel_for`

下列範例說明如何針對呼叫`parallel_for`啟用追蹤。 執行時間不會追蹤的第一個呼叫`parallel_for` , 因為未啟用追蹤。 的呼叫`EnableTracing`可讓執行時間追蹤的第二個`parallel_for`呼叫。

[!code-cpp[concrt-etw#1](../../parallel/concrt/codesnippet/cpp/parallel-diagnostic-tools-concurrency-runtime_1.cpp)]

執行時間會追蹤您呼叫`EnableTracing`和`DisableTracing`的次數。 因此, 如果您多次`EnableTracing`呼叫, 您必須呼叫`DisableTracing`相同的次數, 才能停用追蹤。

## <a name="see-also"></a>另請參閱

[並行執行階段](../../parallel/concrt/concurrency-runtime.md)
