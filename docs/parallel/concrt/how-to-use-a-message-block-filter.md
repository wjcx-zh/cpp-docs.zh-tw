---
title: 如何：使用訊息區篩選條件
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: a5814536e88add5b15f577588d571a06eda6151c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226707"
---
# <a name="how-to-use-a-message-block-filter"></a>如何：使用訊息區篩選條件

本檔示範如何使用篩選函數來啟用非同步訊息區塊，以依據該訊息的承載來接受或拒絕訊息。

當您建立 message block 物件（例如[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)、 [concurrency：： call](../../parallel/concrt/reference/call-class.md)或[concurrency：：轉換器](../../parallel/concrt/reference/transformer-class.md)）時，您可以提供*篩選函數*來判斷訊息區塊是否接受或拒絕訊息。 篩選函數是保證訊息區塊只接收特定值的實用方式。

篩選函數很重要，因為它們可讓您將訊息區塊連接至表單*資料流程網路*。 在資料流程網路中，訊息區塊只會處理符合特定準則的訊息，以控制資料的流程。 將此項與控制流程模型進行比較，其中的資料流程會使用條件陳述式、迴圈等的控制結構來進行管制。

本檔提供如何使用訊息篩選的基本範例。 如需使用訊息篩選器和資料流程模型來連接訊息區塊的其他範例，請參閱[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)和[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

## <a name="example"></a>範例

請考慮下列函式， `count_primes` 其中說明不會篩選傳入訊息之訊息區塊的基本用法。 訊息區塊會將質數附加至[std：： vector](../../standard-library/vector-class.md)物件。 函式會 `count_primes` 將數個數字傳送至訊息區塊，接收來自訊息區塊的輸出值，並將質數的數位列印到主控台。

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer`物件會處理所有輸入值，不過，它只需要質數的值。 雖然可以撰寫應用程式，讓訊息傳送者只傳送質數，但訊息接收者的需求不一定是已知的。

## <a name="example"></a>範例

下列函式會執行與函式 `count_primes_filter` 相同的工作 `count_primes` 。 不過， `transformer` 此版本中的物件會使用篩選函數，只接受質數的值。 執行動作的函式只會接收質數;因此，它不需要呼叫 `is_prime` 函數。

因為 `transformer` 物件只會收到質數，所以 `transformer` 物件本身可以保留質數。 換句話說， `transformer` 在此範例中，不需要在物件中加入質數 `vector` 。

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer`物件現在只會處理質數的值。 在上述範例中， `transformer` 物件會處理所有訊息。 因此，上一個範例必須接收與它所傳送的相同訊息數目。 這個範例會使用[concurrency：： send](reference/concurrency-namespace-functions.md#send)函式的結果，來判斷要從物件接收多少訊息 `transformer` 。 `send` **`true`** 當訊息緩衝區接受訊息，且 **`false`** 訊息緩衝區拒絕訊息時，此函數會傳回。 因此，訊息緩衝區接受訊息的次數會符合質數的計數。

## <a name="example"></a>範例

下列程式碼顯示完整範例。 此範例會呼叫函式 `count_primes` 和 `count_primes_filter` 函數。

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `primes-filter.cpp` 然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl.exe/EHsc primes-filter .cpp**

## <a name="robust-programming"></a>穩固程式設計

篩選函數可以是 lambda 函式、函式指標或函式物件。 每個篩選函數都會採用下列其中一種形式：

```Output
bool (T)
bool (T const &)
```

若要排除不必要的資料複製，請在您有以傳值方式傳輸的匯總類型時，使用第二個表單。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[轉換器類別](../../parallel/concrt/reference/transformer-class.md)
