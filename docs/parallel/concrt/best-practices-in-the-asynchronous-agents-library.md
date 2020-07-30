---
title: 非同步代理程式程式庫中的最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 99780de11d85831a6901f370d2491f15ef88c0b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231737"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>非同步代理程式程式庫中的最佳做法

本檔將說明如何有效使用非同步代理程式程式庫。 代理程式程式庫會升級以動作專案為基礎的程式設計模型和內含式訊息傳遞，以進行粗略的資料流程和管線工作。

如需代理程式程式庫的詳細資訊，請參閱[非同步代理](../../parallel/concrt/asynchronous-agents-library.md)程式程式庫。

## <a name="sections"></a><a name="top"></a>各節

本文件包含下列章節：

- [使用代理程式隔離狀態](#isolation)

- [使用節流機制來限制資料管線中的訊息數目](#throttling)

- [不要在資料管線中執行精細的工作](#fine-grained)

- [不要以傳值方式傳遞大型訊息承載](#large-payloads)

- [當擁有權未定義時，在資料網路中使用 shared_ptr](#ownership)

## <a name="use-agents-to-isolate-state"></a><a name="isolation"></a>使用代理程式隔離狀態

代理程式程式庫可讓您透過非同步訊息傳遞機制來連接隔離的元件，藉此提供共用狀態的替代專案。 當非同步代理程式將其內部狀態與其他元件隔離時，是最有效率的。 藉由隔離狀態，多個元件通常不會對共用資料採取動作。 狀態隔離可讓您的應用程式進行調整，因為它會減少對共用記憶體的爭用。 狀態隔離也會降低鎖死和競爭情況的機率，因為元件不需要同步處理對共用資料的存取。

您通常會在 agent 類別的或區段中保存資料成員 **`private`** **`protected`** ，並使用訊息緩衝區來傳達狀態變更，藉以隔離代理程式中的狀態。 下列範例會顯示 `basic_agent` 衍生自[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)的類別。 `basic_agent`類別會使用兩個訊息緩衝區來與外部元件通訊。 一個訊息緩衝區會保存傳入訊息;另一個訊息緩衝區會保留外寄訊息。

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

如需如何定義和使用代理程式的完整範例，請參閱[逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[逐步解說：建立資料流程代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)程式。

[[頂端](#top)]

## <a name="use-a-throttling-mechanism-to-limit-the-number-of-messages-in-a-data-pipeline"></a><a name="throttling"></a>使用節流機制來限制資料管線中的訊息數目

許多訊息緩衝區類型（例如[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)）可以保留不限數量的訊息。 當訊息產生者將訊息傳送至資料管線的速度比取用者可以處理這些訊息時，應用程式可能會進入記憶體不足或記憶體不足的狀態。 您可以使用節流機制（例如，信號）來限制資料管線中同時啟用的訊息數目。

下列基本範例示範如何使用信號來限制資料管線中的訊息數目。 資料管線會使用[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函式來模擬至少使用100毫秒的作業。 由於傳送者產生的訊息速度比取用者可以處理這些訊息更快，因此這個範例會定義 `semaphore` 類別，讓應用程式限制作用中訊息的數目。

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore`物件會限制管線同時處理最多兩個訊息。

此範例中的產生者會傳送相對較少的訊息給取用者。 因此，此範例不會示範可能的記憶體不足或記憶體不足的狀況。 不過，當資料管線包含相對大量的訊息時，這項機制很有用。

如需如何建立此範例中使用之信號類別的詳細資訊，請參閱[如何：使用內容類別來執行合作的信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

[[頂端](#top)]

## <a name="do-not-perform-fine-grained-work-in-a-data-pipeline"></a><a name="fine-grained"></a>不要在資料管線中執行精細的工作

當資料管線所執行的工作相當粗略時，代理程式程式庫最有用。 例如，一個應用程式元件可能會從檔案或網路連線讀取資料，而偶爾會將該資料傳送至另一個元件。 代理程式程式庫用來傳播訊息的通訊協定，會導致訊息傳遞機制比[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md)（PPL）所提供的工作平行結構擁有更多的額外負荷。 因此，請確定資料管線所執行的工作夠長，可彌補此額外負荷。

雖然資料管線在其工作是粗略的時最有效率，但資料管線的每個階段都可以使用 PPL 結構（例如工作組和平行演算法）來執行更精細的工作。 如需在每個處理階段使用微調平行處理的粗略資料網路範例，請參閱[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[頂端](#top)]

## <a name="do-not-pass-large-message-payloads-by-value"></a><a name="large-payloads"></a>不要以傳值方式傳遞大型訊息承載

在某些情況下，執行時間會建立每個訊息的複本，它會從一個訊息緩衝區傳遞至另一個訊息緩衝區。 例如， [concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)類別會將每個訊息的複本提供給每個目標。 當您使用訊息傳遞函數（例如[concurrency：： send](reference/concurrency-namespace-functions.md#send)和[concurrency：： receive](reference/concurrency-namespace-functions.md#receive) ）來寫入訊息，並從訊息緩衝區讀取訊息時，執行時間也會建立訊息資料的複本。 雖然這項機制有助於消除同時寫入共用資料的風險，但當訊息承載相對較大時，可能會導致記憶體效能不佳。

當您傳遞具有大型承載的訊息時，您可以使用指標或參考來改善記憶體效能。 下列範例會比較以傳值方式傳遞大型訊息，以將指標傳遞至相同的訊息類型。 此範例會定義兩個 `producer` `consumer` 在物件上作用的代理程式類型和 `message_data` 。 此範例會比較產生者將數個物件傳送給取用者所需的時間，以及產生器 `message_data` 代理程式將數個指標傳送給取用者所需的時間 `message_data` 。

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

這個範例會產生下列範例輸出：

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

使用指標的版本會執行得更好，因為它不需要讓執行時間為每個 `message_data` 從生產者傳遞給取用者的物件建立完整複本。

[[頂端](#top)]

## <a name="use-shared_ptr-in-a-data-network-when-ownership-is-undefined"></a><a name="ownership"></a>當擁有權未定義時，在資料網路中使用 shared_ptr

當您透過訊息傳遞管線或網路的指標傳送訊息時，通常會在網路前端配置每個訊息的記憶體，並在網路末端釋放該記憶體。 雖然這項機制經常運作良好，但有時候很難以或無法使用它。 例如，請考慮資料網路包含多個端點節點的情況。 在此情況下，沒有明確的位置可釋放訊息的記憶體。

若要解決這個問題，您可以使用一個機制（例如[std：： shared_ptr](../../standard-library/shared-ptr-class.md)），讓指標擁有多個元件。 當 `shared_ptr` 擁有資源的最終物件損毀時，也會釋放資源。

下列範例示範如何使用 `shared_ptr` ，在多個訊息緩衝區之間共用指標值。 此範例會將[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)物件連接至三個[concurrency：： call](../../parallel/concrt/reference/call-class.md)物件。 `overwrite_buffer`類別會將訊息提供給它的每個目標。 因為資料網路結尾有多個資料擁有者，所以這個範例會使用 `shared_ptr` 來讓每個 `call` 物件共用訊息的擁有權。

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

這個範例會產生下列範例輸出：

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>另請參閱

[並行執行階段最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[逐步解說：建立以代理程式為基礎的應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[平行模式程式庫中的最佳作法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[並行執行階段中的一般最佳作法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
