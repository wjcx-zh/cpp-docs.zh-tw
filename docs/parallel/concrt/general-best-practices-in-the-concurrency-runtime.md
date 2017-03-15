---
title: "並行執行階段中的一般最佳作法 | Microsoft Docs"
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
  - "並行執行階段，一般最佳作法"
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 並行執行階段中的一般最佳作法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明並行執行階段多個方面適用的最佳作法。  
  
##  <a name="top"></a> 章節  
 本文件包括下列章節：  
  
-   [盡可能使用合作式同步處理建構](#synchronization)  
  
-   [避免使用不讓渡的冗長工作](#yield)  
  
-   [使用過度訂閱使封鎖或有高延遲的作業位移](#oversubscription)  
  
-   [盡可能使用並行記憶體管理函式](#memory)  
  
-   [使用 RAII 管理並行物件的存留期](#raii)  
  
-   [不要在全域範圍建立並行物件](#global-scope)  
  
-   [不要在共用資料區段中使用並行物件](#shared-data)  
  
##  <a name="synchronization"></a> 盡可能使用合作式同步處理建構  
 並行執行階段提供許多不需要外部同步處理物件的並行安全建構。  例如，[concurrency::concurrent\_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 類別提供並行安全附加和項目存取作業。  不過，如果您需要資源的獨占存取，執行階段提供了 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md)、[concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 和 [concurrency::event](../../parallel/concrt/reference/event-class.md) 類別。  這些型別是以合作方式運作，因此工作排程器可以在第一個工作等候資料時，將處理資源重新配置給另一個內容。  盡可能使用這些同步處理型別，而不要使用例如 Windows API 所提供、不會以合作方式運作的其他同步處理機制。  如需這些同步處理型別的詳細資訊和程式碼範例，請參閱[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)和[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="yield"></a> 避免使用不讓渡的冗長工作  
 因為工作排程器是以合作方式運作，它不會在工作之間提供公平性。  因此，某個工作可能會防止其他工作開始。  雖然在某些案例中，這是可以接受的，但在其他案例中可能就會造成死結或耗盡。  
  
 下列範例所執行的工作多於配置的處理資源數目。  第一個工作不會讓給工作排程器，因此在第一個工作完成之前，第二個工作不會開始。  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 這個範例會產生下列輸出：  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  
 有數個方式可在兩個工作之間啟用合作。  一個方式是在長時間執行的工作中偶爾讓給工作排程器。  下列範例會將 `task` 函式修改為呼叫 [concurrency::Context::Yield](../Topic/Context::Yield%20Method.md) 方法，將執行讓給工作排程器，以便另一個工作可以執行。  
  
 [!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_2.cpp)]  
  
 這個範例會產生下列輸出：  
  
  **1: 250000000**  
**2: 250000000**  
**1: 500000000**  
**2: 500000000**  
**1: 750000000**  
**2: 750000000**  
**1: 1000000000**  
**2: 1000000000** `Context::Yield` 方法只會讓給目前執行緒所屬的排程器上的另一個使用中執行緒、輕量型工作或另一個作業系統執行緒。  這個方法不會讓給排定要在 [concurrency::task\_group](../Topic/task_group%20Class.md) 或 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件中執行但尚未開始的工作。  
  
 有其他方式可在長時間執行的工作之間啟用合作。  您可以將大型工作細分為較小的子任務。  您也可以在冗長工作期間啟用過度訂閱。  過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。  當冗長工作的延遲性較高 \(例如從磁碟或網路連接讀取資料\)，過度訂閱特別實用。  如需輕量型工作和過度訂閱的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="oversubscription"></a> 使用過度訂閱使封鎖或有高延遲的作業位移  
 並行執行階段提供同步處理基本型別 \(例如 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md)\)，可讓工作以合作方式封鎖和彼此相讓。  當某個工作以合作方式封鎖或讓渡時，工作排程器可以在第一個工作等候資料時，將處理資源重新配置給另一個內容。  
  
 在某些案例中，您無法使用並行執行階段所提供的合作式封鎖機制。  例如，您所使用的外部程式庫可能使用不同的同步處理機制。  另一個例子是當您執行延遲性較高的作業，例如使用 Windows API `ReadFile` 函式，從網路連接讀取資料時。  在這些案例中，過度訂閱可以在某個工作閒置時讓其他工作執行。  過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。  
  
 考慮下列 `download` 函式下載位於給定 URL 的檔案。  這個範例使用 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法，暫時增加使用中執行緒的數目。  
  
 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 因為 `GetHttpFile` 函式執行潛在延遲的作業，過度訂閱可以在目前工作等候資料時，讓其他工作執行。  如需此範例的完整版本，請參閱 [如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="memory"></a> 盡可能使用並行記憶體管理函式  
 當您的精細工作經常配置存留期相當短的小物件時，請使用記憶體管理函式 [concurrency::Alloc](../Topic/Alloc%20Function.md) 和 [concurrency::Free](../Topic/Free%20Function.md)。  並行執行階段會針對每個執行中的執行緒保存不同的記憶體快取。  `Alloc` 和 `Free` 函式會在這些快取中配置及釋放記憶體，而不使用鎖定或記憶體屏障。  
  
 如需這些記憶體管理函式的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  如需使用這些函式的範例，請參閱 [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="raii"></a> 使用 RAII 管理並行物件的存留期  
 並行執行階段使用例外狀況處理來實作取消等功能。  因此，當您呼叫執行階段或呼叫另一個會呼叫執行階段的程式庫時，請撰寫無例外狀況之虞的程式碼。  
  
 「*資源擷取為初始設定*」\(Resource Acquisition Is Initialization，RAII\) 模式是在給定範圍下安全管理並行物件存留期的一種方式。  在 RAII 模式下，資料結構會配置於堆疊上。  該資料結構會在建立時初始化或擷取資源，並在資料結構終結時終結或釋放該資源。  RAII 模式可保證在封閉範圍結束之前呼叫解構函式。  當函式包含多個 `return` 陳述式時，這種模式很實用。  這個模式也有助於您撰寫無例外狀況之虞的程式碼。  當 `throw` 陳述式導致堆疊回溯時，就會呼叫 RAII 物件的解構函式，因此一定會正確刪除或釋放資源。  
  
 執行階段定義數個使用 RAII 模式的類別，例如 [concurrency::critical\_section::scoped\_lock](../Topic/critical_section::scoped_lock%20Class.md) 和 [concurrency::reader\_writer\_lock::scoped\_lock](../Topic/reader_writer_lock::scoped_lock%20Class.md)。  這些 Helper 類別稱為「*範圍鎖定*」\(Scoped Lock\)。  當您使用 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 或 [concurrency::reader\_writer\_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 物件時，這些類別提供數個好處。  這些類別的建構函式會取得對所提供 `critical_section` 或 `reader_writer_lock` 物件的存取，而解構函式則會釋放對該物件的存取。  因為範圍鎖定會在終結時自動釋放其互斥物件的存取權，所以您不會以手動方式解除鎖定基礎物件。  
  
 請考慮下列類別 `account`，這是由外部程式庫所定義，因此無法修改。  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 下列範例會在 `account` 物件上平行執行多個交易。  範例使用 `critical_section` 物件，以同步處理對 `account` 物件的存取，因為 `account` 類別不是並行安全的。  每個平行作業都會使用 `critical_section::scoped_lock` 物件，以確保 `critical_section` 物件會在作業成功或失敗時解除鎖定。  當帳戶餘額為負數時，`withdraw` 作業會藉由擲回例外狀況而失敗。  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出：  
  
  **在庫存前的平衡: 1924**   
**在庫存以後的平衡:2924**  
**在收回前的平衡:2924**  
**在收回後的平衡:\-76**  
**在收回前的平衡:\-76**  
**錯誤詳細資料:**   
 **負數平衡:\-76** 如需使用 RAII 模式管理並行物件存留期的其他範例，請參閱[逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)、[如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)和 [如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="global-scope"></a> 不要在全域範圍建立並行物件  
 當您建立並行物件在全域範圍時，您在應用程式中造成問題 \(例如死結或記憶體存取違規的發生\)。  
  
 例如，當您建立並行執行階段物件時，執行階段會建立預設排程器 \(如果尚未建立\)。  在全域物件建構期間建立的執行階段物件會因此導致執行階段建立這種預設排程器。  不過，此處理序會採用內部鎖定，這會妨礙支援並行執行階段基礎結構的其他物件初始化。  另一個尚未初始化的基礎結構物件可能需要此內部鎖定，所以應用程式可能會發生死結。  
  
 下列範例示範如何建立全域 [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) 物件。  這個模式不只套用至 `Scheduler` 類別，但套用至並行執行階段所提供的所有其他型別。  我們建議您不要遵循這個模式，因為它會造成應用程式不可預料的結果。  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/CPP/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 如需如何正確建立 `Scheduler` 物件的範例，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="shared-data"></a> 不要在共用資料區段中使用並行物件  
 並行執行階段不支援並行物件用於共用資料區段，例如 [data\_seg](../../preprocessor/data-seg.md) `#pragma` 指示詞所建立的資料區段。  跨處理序界限共用的並行物件可能會導致執行階段處於不一致或無效狀態。  
  
 \[[上方](#top)\]  
  
## 請參閱  
 [並行執行階段最佳作法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [平行模式程式庫 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)   
 [比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [平行模式程式庫中的最佳作法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [非同步代理程式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)