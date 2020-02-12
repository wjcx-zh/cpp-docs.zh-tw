---
title: 並行執行階段
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: a17b4439baaec9caacfeca08983d0255b5a145de
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141611"
---
# <a name="concurrency-runtime"></a>並行執行階段

C++ 的並行執行階段可協助您寫入強固、可擴充且回應靈敏的平行應用程式。 它會引發抽象的層級，讓您不需要管理並行存取相關的基礎結構詳細資料。 您也可以使用它來指定符合您應用程式服務需求品質的排程原則。 使用這些資源以協助您開始使用並行執行階段。

如需參考檔，請參閱[參考](../../parallel/concrt/reference/reference-concurrency-runtime.md)。

> [!TIP]
> 並行執行階段非常依賴 C++11 功能，並採用更現代的 C++ 樣式。 若要深入瞭解，請閱讀[歡迎C++回到](../../cpp/welcome-back-to-cpp-modern-cpp.md)。

## <a name="choosing-concurrency-runtime-features"></a>選擇並行執行階段功能

|||
|-|-|
|[概觀](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|教導為何並行執行階段很重要，並說明其重要功能。|
|[與其他並行模型比較](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|顯示並行執行階段如何與其他並行模型進行比較，例如 Windows 執行緒集區和 OpenMP，以讓您可以使用最符合您應用程式需求的並行存取模型。|
|[從 OpenMP 移轉至並行執行階段](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|比較 OpenMP 與並行執行階段，並提供有關如何移轉現有的 OpenMP 程式碼以使用並行執行階段的範例。|
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|為您介紹提供平行迴圈、工作和平行容器的 PPL。|
|[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)|為您介紹如何使用非同步代理程式和訊息傳遞來輕鬆地將資料流程與流水線操作工作納入您的應用程式中。|
|[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|為您介紹工作排程器，可讓您微調使用並行執行階段的桌面應用程式的效能。|

## <a name="task-parallelism-in-the-ppl"></a>PPL 中的工作平行處理原則

|||
|-|-|
|[工作平行處理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [如何：使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [如何：使用 parallel_invoke 執行平行作業](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [如何：建立在延遲之後才會完成的工作](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|描述工作和工作群組，可協助您撰寫非同步程式碼並將平行工作分解成較小的片段。|
|[逐步解說：實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)|示範如何結合並行執行階段功能以做到更多。|
|[逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|顯示如何將 MFC 應用程式中的 UI 執行緒所執行的工作移至背景工作執行緒。|
|[平行模式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用 PPL 的秘訣和最佳作法。|

## <a name="data-parallelism-in-the-ppl"></a>PPL 中的資料平行處理原則

|||
|-|-|
|[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [如何：撰寫 parallel_for 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [如何：撰寫 parallel_for_each 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [如何：平行執行對應和縮減作業](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|描述 `parallel_for`、 `parallel_for_each`、 `parallel_invoke`，和其他平行演算法。 使用平行演算法來解決牽涉到資料集合的 *「資料平行」* (data parallel) 問題。|
|[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [如何：使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [如何：使用 combinable 改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [如何：使用 combinable 結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|描述 `combinable` 類別，以及 `concurrent_vector`、 `concurrent_queue`、 `concurrent_unordered_map`，和其他平行容器。 當您需要提供安全執行緒存取其項目的容器時，請使用平行容器和物件。|
|[平行模式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用 PPL 的秘訣和最佳作法。|

## <a name="canceling-tasks-and-parallel-algorithms"></a>取消工作和平行演算法

|||
|-|-|
|[PPL 中的取消](cancellation-in-the-ppl.md)|描述 PPL 中取消的角色，包括如何起始和回應取消的要求。|
|[如何：使用取消來中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|示範兩種用來取消資料平行工作的方式。|

## <a name="universal-windows-platform-apps"></a>通用 Windows 平台應用程式

|||
|-|-|
|[在 C++ for UWP 應用程式中建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|說明當您使用並行執行階段在 UWP 應用程式中產生非同步作業時，要牢記在心的部分重點。|
|[逐步解說：使用工作和 XML HTTP 要求連接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|說明如何將 PPL 工作與 `IXMLHTTPRequest2` 和 `IXMLHTTPRequest2Callback` 介面結合，以將 HTTP GET 和 POST 要求傳送至 UWP 應用程式中的 web 服務。|
|[Windows 執行階段應用程式範例](https://code.msdn.microsoft.com/windowsapps)|包含適用于 Windows 8.x 的可下載程式代碼範例和示範應用程式。 C + + 範例使用並行執行階段功能 (例如 PPL 工作) 來處理在背景中的資料以保留 UX 的回應性。|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>非同步代理程式程式庫中的資料流程程式撰寫

|||
|-|-|
|[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)<br /><br /> [如何：實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [如何：為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [如何：在已完成的工作之中選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)|描述非同步代理程式、訊息區塊與訊息傳遞功能，也就是在並行執行階段中執行資料流程作業的建置組塊。|
|[逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|示範如何建立基本的代理程式應用程式。|
|[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|示範如何建立執行映像處理的非同步訊息區的網路。|
|[逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|使用哲學家用餐問題，說明如何使用並行執行階段避免應用程式中的死結。|
|[逐步解說：建立自訂訊息區](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|示範如何建立依優先順序排序內送訊息的自訂訊息區塊類型。|
|[非同步代理程式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|提供使用代理程式的秘訣和最佳作法。|

## <a name="exception-handling-and-debugging"></a>例外狀況處理和偵錯

|||
|-|-|
|[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|描述如何使用並行執行階段中的例外狀況。|
|[平行診斷工具](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|教您如何微調您的應用程式及充分有效地運用並行執行階段。|

## <a name="tuning-performance"></a>微調效能

|||
|-|-|
|[平行診斷工具](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|教您如何微調您的應用程式及充分有效地運用並行執行階段。|
|[排程器執行個體](../../parallel/concrt/scheduler-instances.md)<br /><br /> [如何：管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [排程器原則](../../parallel/concrt/scheduler-policies.md)<br /><br /> [如何：指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [如何：建立使用特定排程器原則的代理程式](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|示範如何使用管理排程器執行個體和排程器原則。 針對桌面應用程式，排程器原則可讓您將特定的規則與特定類型的工作負載產生關聯。 例如，您可以建立一個排程器執行個體，在高權限的執行緒優先順序上執行一些工作，並使用預設排程器在正常的執行緒優先順序上執行其他工作。|
|[排程群組](../../parallel/concrt/schedule-groups.md)<br /><br /> [如何：使用排程群組來影響執行順序](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|示範如何使用排程群組來同質化、或是將相關的工作分組在一起。 例如，當工作受益於在相同處理器節點上執行時，相關工作之間可能需要較高程度的的位置。|
|[輕量型工作](../../parallel/concrt/lightweight-tasks.md)|說明輕量型工作如何有用地建立不需要負載平衡或取消的工作，以及其同時也有用地調整現有的程式碼，以搭配並行執行階段的工作。|
|[內容](../../parallel/concrt/contexts.md)<br /><br /> [如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|描述如何由並行執行階段控制的執行緒行為。|
|[記憶體管理函式](../../parallel/concrt/memory-management-functions.md)<br /><br /> [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|描述可協助您以並行方式配置和釋放記憶體並行執行階段記憶體的管理函式。|

## <a name="additional-resources"></a>其他資源

|||
|-|-|
|[Hilo 的非同步程式設計模式和祕訣 (使用 C++ 和 XAML 的 Windows 市集應用程式)](/previous-versions/windows/apps/jj160321(v=win.10))|瞭解我們如何使用並行執行階段在 Hilo （使用C++和 XAML 的 Windows 執行階段應用程式）中執行非同步作業。|
|[機器碼平行程式設計部落格](https://go.microsoft.com/fwlink/p/?linkid=183873)|提供有關在並行執行階段中之平行程式設計的其他深入部落格文章。|
|[C++ 和機器碼平行程式設計論壇](https://go.microsoft.com/fwlink/p/?linkid=183874)|讓您參與有關並行執行階段的社群討論。|
|[平行程式設計](/dotnet/standard/parallel-programming/index)|教您有關 .NET Framework 中提供的平行程式設計模型。|

## <a name="see-also"></a>另請參閱

[參考](../../parallel/concrt/reference/reference-concurrency-runtime.md)
