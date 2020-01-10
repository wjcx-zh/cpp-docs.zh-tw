---
title: 並行執行階段中的一般最佳作法
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: bb00c3ddb9a50a159174deccf8954f1e3bf1689d
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302220"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>並行執行階段中的一般最佳作法

本檔說明適用于並行執行階段多個區域的最佳作法。

##  <a name="top"></a> 章節

本文件包含下列章節：

- [盡可能使用合作的同步處理結構](#synchronization)

- [避免冗長的工作不會產生](#yield)

- [使用超額訂閱來位移封鎖或具有高延遲的作業](#oversubscription)

- [盡可能使用並行記憶體管理函數](#memory)

- [使用 RAII 來管理並行物件的存留期](#raii)

- [不要在全域範圍建立並行物件](#global-scope)

- [請勿在共用資料區段中使用並行物件](#shared-data)

##  <a name="synchronization"></a>盡可能使用合作的同步處理結構

並行執行階段提供許多不需要外部同步處理物件的並行保護結構。 例如， [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別提供並行安全的附加和元素存取作業。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。 不過，在需要資源獨佔存取權的情況下，執行時間會提供[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)、 [concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)和[concurrency：：事件](../../parallel/concrt/reference/event-class.md)類別。 這些類型會以合作方式運作;因此，當第一個工作等候資料時，工作排程器可以將處理資源重新配置給另一個內容。 可能的話，請使用這些同步處理類型，而不是其他同步處理機制（例如 Windows API 所提供的），而不會以合作方式運作。 如需這些同步處理類型和程式碼範例的詳細資訊，請參閱[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)和[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)。

[[靠上](#top)]

##  <a name="yield"></a>避免冗長的工作不會產生

因為工作排程器會以合作方式運作，所以不會在工作之間提供公平的作業。 因此，工作可能會阻止其他工作啟動。 雖然這在某些情況下是可接受的，但在其他情況下，這可能會造成鎖死或耗盡。

下列範例會比配置的處理資源數執行更多工。 第一個工作不會產生工作排程器，因此第一個工作完成前，第二個工作不會啟動。

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

這個範例會產生下列輸出：

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

有數種方式可讓兩個工作之間的合作。 其中一種方式是在長時間執行的工作中，偶爾產生工作排程器。 下列範例會將 `task` 函式修改為呼叫[concurrency：： CoNtext：： yield](reference/context-class.md#yield)方法，以產生工作排程器的執行，讓其他工作可以執行。

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

`Context::Yield` 方法只會在目前線程所屬的排程器上產生另一個使用中線程，也就是輕量工作或另一個作業系統執行緒。 這個方法不會產生排程要在[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件中執行，但尚未啟動的工作。

還有其他方法可在長時間執行的工作之間啟用合作。 您可以將大型工作分成較小的子任務。 您也可以在冗長的工作期間啟用超額訂閱。 過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。 當冗長的工作包含大量延遲（例如從磁片或網路連線讀取資料）時，超額訂閱特別有用。 如需有關輕量工作和超額訂閱的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[靠上](#top)]

##  <a name="oversubscription"></a>使用超額訂閱來位移封鎖或具有高延遲的作業

並行執行階段提供同步處理原始物件（例如[Concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)），可讓工作以合作方式封鎖和產生彼此。 當一個工作以合作方式封鎖或產生時，工作排程器可以在第一項工作等候資料時，將處理資源重新配置到另一個內容。

在某些情況下，您無法使用並行執行階段所提供的合作式封鎖機制。 例如，您使用的外部程式庫可能會使用不同的同步處理機制。 另一個範例是當您執行可能有很高延遲的作業時，例如，當您使用 Windows API `ReadFile` 函式從網路連接讀取資料時。 在這些情況下，超額訂閱可以讓其他工作在另一項工作閒置時執行。 過度訂閱可讓您建立比可用硬體執行緒數目更多的執行緒。

請考慮下列函式 `download`，它會在指定的 URL 下載檔案。 這個範例使用[concurrency：： CoNtext：：超額](reference/context-class.md#oversubscribe)方法來暫時增加使用中線程的數目。

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

因為 `GetHttpFile` 函式會執行潛在的潛在作業，所以過度訂閱可以讓其他工作在等候資料的目前工作時執行。 如需此範例的完整版本，請參閱[如何：使用超額訂閱來抵銷延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[靠上](#top)]

##  <a name="memory"></a>盡可能使用並行記憶體管理函數

當您有更細緻的工作經常配置較短存留期的小型物件時，請使用記憶體管理函式[concurrency：：](reference/concurrency-namespace-functions.md#alloc) allocate 和[Concurrency：： Free](reference/concurrency-namespace-functions.md#free)。 並行執行階段會針對每個執行中的執行緒保存個別的記憶體快取。 `Alloc` 和 `Free` 函數會從這些快取配置和釋放記憶體，而不會使用鎖定或記憶體屏障。

如需這些記憶體管理功能的詳細資訊，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。 如需使用這些函式的範例，請參閱[如何：使用配置和免費來改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

[[靠上](#top)]

##  <a name="raii"></a>使用 RAII 來管理並行物件的存留期

並行執行階段會使用例外狀況處理來執行取消之類的功能。 因此，當您呼叫執行時間或呼叫另一個呼叫執行時間的程式庫時，請撰寫例外狀況安全的程式碼。

「*資源取得」是初始化*（RAII）模式，是在指定範圍下安全地管理並行物件存留期的一種方式。 在 RAII 模式下，會在堆疊上配置資料結構。 該資料結構會在建立時初始化或取得資源，並在終結資料結構時，終結或釋放該資源。 RAII 模式可保證在封閉範圍結束之前呼叫此析構函式。 當函數包含多個 `return` 語句時，此模式非常有用。 此模式也可協助您撰寫例外狀況安全的程式碼。 當 `throw` 語句導致堆疊回溯時，會呼叫 RAII 物件的析構函式;因此，一律會正確地刪除或釋放資源。

執行時間會定義數個使用 RAII 模式的類別，例如[concurrency：： critical_section：： scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class)和[concurrency：： reader_writer_lock：： scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)。 這些 helper 類別稱為*範圍鎖定*。 當您使用[concurrency：： critical_section](../../parallel/concrt/reference/critical-section-class.md)或[concurrency：： reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)物件時，這些類別可提供數個優點。 這些類別的函式會取得所提供 `critical_section` 或 `reader_writer_lock` 物件的存取權;此析構函式會釋放對該物件的存取。 由於限定範圍的鎖定會在終結時自動釋放其相互排除物件的存取權，因此您不需手動解除鎖定基礎物件。

請考慮下列類別，`account`，這是由外部程式庫所定義，因此無法修改。

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

下列範例會以平行方式在 `account` 物件上執行多個交易。 此範例會使用 `critical_section` 物件來同步處理 `account` 物件的存取，因為 `account` 類別不是並行安全。 每個平行作業都會使用 `critical_section::scoped_lock` 物件，以確保當作業成功或失敗時，會解除鎖定 `critical_section` 物件。 當帳戶餘額為負數時，`withdraw` 作業會藉由擲回例外狀況而失敗。

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

這個範例會產生下列範例輸出：

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

如需使用 RAII 模式來管理並行物件存留期的其他範例，請參閱[逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)、[如何：使用內容類別來執行合作的信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)，以及[如何：使用超額訂閱來位移延遲](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)。

[[靠上](#top)]

##  <a name="global-scope"></a>不要在全域範圍建立並行物件

當您在全域範圍建立並行物件時，可能會造成應用程式中發生像是死結或記憶體存取違規這類問題。

例如，當您建立並行執行階段物件時，執行階段會自動建立預設排程器 (如果尚未建立)。 於是在建構全域物件期間建立的執行階段物件會導致執行階段建立這種預設排程器。 不過，這個處理序會採用內部鎖定，而這可能會妨礙支援並行執行階段基礎結構的其他物件初始化。 另一個尚未初始化的基礎結構物件可能需要這個內部鎖定，所以可能造成應用程式中發生死結。

下列範例示範如何建立全域[concurrency：：](../../parallel/concrt/reference/scheduler-class.md)排程器物件。 這個模式不只套用至 `Scheduler` 類別，也會套用至並行執行階段所提供的所有其他類型。 我們建議您不要遵循這個模式，因為它會造成應用程式發生無法預期的行為。

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

如需建立 `Scheduler` 物件的正確方式範例，請參閱[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

[[靠上](#top)]

##  <a name="shared-data"></a>請勿在共用資料區段中使用並行物件

並行執行階段不支援在共用資料區段中使用並行物件（例如，由[data_seg](../../preprocessor/data-seg.md)`#pragma` 指示詞所建立的資料區段）。 跨進程界限共用的並行物件可能會使執行時間處於不一致或不正確狀態。

[[靠上](#top)]

## <a name="see-also"></a>請參閱

[並行執行階段最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)<br/>
[比較同步處理資料結構與 Windows API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[如何：使用 Alloc 和 Free 改善記憶體效能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[如何：使用過度訂閱使延遲產生位移](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[平行模式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[非同步代理程式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
