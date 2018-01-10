---
title: "並行執行階段中的一般最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5c2c626ceb0243e91e56d70f0d8ae71208b157f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>並行執行階段中的一般最佳作法
本文件說明套用到多個並行執行階段區域的最佳作法。  
  
##  <a name="top"></a> 章節  
 本文件包含下列章節：  
  
- [使用合作式同步處理建構盡可能](#synchronization)  
  
- [避免長時間不會產生的工作](#yield)  
  
- [使用過度訂閱位移封鎖或有高延遲的作業](#oversubscription)  
  
- [使用並行的記憶體管理函式時可能](#memory)  
  
- [使用 RAII 管理並行存取物件的存留期](#raii)  
  
- [不在全域範圍建立並行物件](#global-scope)  
  
- [請勿使用共用的資料區段中的並行存取物件](#shared-data)  
  
##  <a name="synchronization"></a>使用合作式同步處理建構盡可能  
 並行執行階段提供許多並行安全建構不需要外部的同步處理物件。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別會提供並行安全附加和項目存取作業。 不過，您需要獨佔存取資源的情況下，執行階段提供[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)， [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)，和[並行:: 事件](../../parallel/concrt/reference/event-class.md)類別。 這些類型的行為以合作方式;因此，工作排程器可以重新配置到另一個內容的處理資源，因為第一個工作等候資料。 可能的話，請使用這些同步處理類型而不是其他同步處理機制，例如所提供的 Windows API 中，未以合作方式運作。 如需有關這些同步處理類型和程式碼範例的詳細資訊，請參閱[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)和[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。  
  
 [[靠上](#top)]  
  
##  <a name="yield"></a>避免長時間不會產生的工作  
 工作排程器的行為以合作方式，因為它不會提供在工作之間的公平性。 因此，工作可以防止其他工作啟動。 雖然這是可接受在某些情況下，在其他情況下，這會造成死結或耗盡。  
  
 下列範例會執行更多的工作已配置的處理資源的數目。 第一項工作不會產生工作排程器，因此第二個工作不會開始第一項工作完成為止。  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 這個範例會產生下列輸出：  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  

 有幾種方式以啟用兩個工作之間的合作。 一種方式為偶爾產生工作排程器在長時間執行工作。 下列範例會修改`task`函式呼叫[yield](reference/context-class.md#yield)方法來產生工作排程器執行，以便在執行另一項工作。  

  
 [!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
1: 250000000  
2: 250000000  
1: 500000000  
2: 500000000  
1: 750000000  
2: 750000000  
1: 1000000000  
2: 1000000000  
```  
  
 `Context::Yield`方法會產生目前的執行緒、 所屬輕量型工作或另一個作業系統執行緒排程器上的另一個只使用中執行緒。 這個方法不會運作，排程為在執行[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件但尚未開始。  
  
 還有其他方式，以便在長時間執行工作之間的合作。 您可以中斷大型工作分為較小的子工作。 您也可以啟用過度訂閱期間的時間較長的工作。 過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。 過度訂閱，特別適用於時間較長的工作包含大量的延遲時間，例如，從磁碟或網路連線讀取資料。 如需輕量型工作，以及過度訂閱的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 [[靠上](#top)]  
  
##  <a name="oversubscription"></a>使用過度訂閱位移封鎖或有高延遲的作業  
 並行執行階段提供同步處理原始物件，例如[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)，可讓工作以合作方式封鎖和相讓彼此。 一項工作以合作方式封鎖或時，工作排程器可以重新配置到另一個內容的處理資源為第一個工作等候資料。  
  
 一些您無法使用並行執行階段所提供的合作式封鎖機制的情況。 例如，您所使用之外部程式庫可能會使用不同的同步處理機制。 另一個範例是當您執行的作業，可能會有大量的延遲時間，例如，當您使用 Windows API`ReadFile`函式可從網路連線讀取資料。 在這些情況下，過度訂閱可啟用另一項工作處於閒置狀態時執行其他工作。 過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。  
  
 請考慮下列函式`download`，此工具會下載的檔案，在指定的 URL。 這個範例會使用[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法來暫時增加使用中執行緒數目。  

 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 因為`GetHttpFile`函式會執行可能會潛在的作業，過度訂閱可啟用目前的工作等候資料執行其他工作。 此範例的完整版本，請參閱[How to： 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 [[靠上](#top)]  
  
##  <a name="memory"></a>使用並行的記憶體管理函式時可能  

 使用記憶體管理函式， [concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)和[concurrency:: free](reference/concurrency-namespace-functions.md#free)，當您的精細工作經常配置存留期相當短的小型物件。 並行執行階段會保存不同的記憶體快取的每個執行中的執行緒。 `Alloc`和`Free`函式配置和釋放記憶體，從這些快取，而不使用鎖定或記憶體屏障。  
  
 如需有關這些記憶體管理函式的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 如需使用這些函式的範例，請參閱[How to： 使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
 [[靠上](#top)]  
  
##  <a name="raii"></a>使用 RAII 管理並行存取物件的存留期  
 並行執行階段會使用例外狀況處理來實作功能，例如取消。 當您呼叫執行階段，或呼叫另一個執行階段所呼叫的程式庫，因此，撰寫例外狀況安全程式碼。  
  
 *資源擷取即初始化*(RAII) 模式是一種安全地管理在給定範圍內的並行存取物件的存留期的方式。 下 RAII 模式，是在堆疊上配置的資料結構。 該資料結構初始化或建立和終結或終結的資料結構時，釋放該資源時，取得資源。 RAII 模式可確保解構函式稱為封入範圍結束之前。 此模式時，函式包含多個`return`陳述式。 此模式也可協助您撰寫例外狀況安全程式碼。 當`throw`陳述式會導致堆疊回溯，解構函式就稱為 RAII 物件; 因此，一定會正確地刪除或釋放資源。  
  
 執行階段定義數個使用 RAII 模式，例如，類別[concurrency::critical_section::scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)。 這些 helper 類別稱為*範圍鎖定*。 這些類別提供幾個優點，當您使用[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)或[concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)物件。 這些類別的建構函式會取得以提供存取`critical_section`或`reader_writer_lock`物件，該物件的解構函式版本存取。 因為範圍釋出鎖定其互斥物件的存取權會自動終結時，您不要以手動方式解除鎖定基礎物件。  
  
 請考慮下列類別`account`，這由外部程式庫所定義，因此無法修改。  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 下列範例執行多個交易上`account`平行的物件。 此範例會使用`critical_section`物件同步處理存取`account`物件，因為`account`類別不是並行安全。 每個平行作業會使用`critical_section::scoped_lock`物件來保證`critical_section`物件時，才能解除鎖定作業是成功或失敗。 當帳戶餘額為負數，`withdraw`作業失敗時擲回例外狀況。  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 這個範例會產生下列輸出範例：  
  
```Output  
Balance before deposit: 1924  
Balance after deposit: 2924  
Balance before withdrawal: 2924  
Balance after withdrawal: -76  
Balance before withdrawal: -76  
Error details:  
    negative balance: -76  
```  
  
 如需使用 RAII 模式，來管理並行存取物件的存留期的其他範例，請參閱[逐步解說： 從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)， [How to： 使用內容類別實作合作式號誌](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)，和[How to： 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。  
  
 [[靠上](#top)]  
  
##  <a name="global-scope"></a>不在全域範圍建立並行物件  
 當您在全域範圍建立並行物件時，可能會造成應用程式中發生像是死結或記憶體存取違規這類問題。  
  
 例如，當您建立並行執行階段物件時，執行階段會自動建立預設排程器 (如果尚未建立)。 於是在建構全域物件期間建立的執行階段物件會導致執行階段建立這種預設排程器。 不過，這個處理序會採用內部鎖定，而這可能會妨礙支援並行執行階段基礎結構的其他物件初始化。 另一個尚未初始化的基礎結構物件可能需要這個內部鎖定，所以可能造成應用程式中發生死結。  
  
 下列範例示範如何建立全域[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)物件。 這個模式不只套用至 `Scheduler` 類別，也會套用至並行執行階段所提供的所有其他類型。 我們建議您不要遵循這個模式，因為它會造成應用程式發生無法預期的行為。  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 如需建立正確的方法的範例`Scheduler`物件，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 [[靠上](#top)]  
  
##  <a name="shared-data"></a>請勿使用共用的資料區段中的並行存取物件  
 並行執行階段不支援在共用的資料區段中，例如，資料的區段所建立的並行存取物件的使用[data_seg](../../preprocessor/data-seg.md) `#pragma`指示詞。 共用跨處理序界限的並行存取物件無法使執行階段處於不一致或不正確的狀態。  
  
 [[靠上](#top)]  
  
## <a name="see-also"></a>請參閱  
 [並行執行階段最佳作法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)   
 [比較同步處理資料結構與 windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [如何： 使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [如何： 使用過度訂閱位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [如何： 使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [逐步解說： 從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [平行模式程式庫中的最佳作法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [非同步代理程式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
