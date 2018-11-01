---
title: 如何：使用訊息區篩選條件
ms.date: 11/04/2016
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
ms.openlocfilehash: 512dda6503d5980dbdcc20a55ca0ee836d4d08e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660131"
---
# <a name="how-to-use-a-message-block-filter"></a>如何：使用訊息區篩選條件

本文件將示範如何使用篩選函數，讓非同步訊息區塊接受或拒絕訊息，以根據該訊息的承載。

當您建立訊息區塊物件這類[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)，則[concurrency:: call](../../parallel/concrt/reference/call-class.md)，或有[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)，您可以提供*filter 函數*，判斷訊息區塊接受或拒絕訊息。 篩選函式是實用的方式，以確保該訊息區塊只接收特定值。

篩選函式很重要，因為它們可讓您連接訊息區塊組成*資料流程網路*。 在資料流程網路中，訊息區塊控制資料流處理只有在符合特定準則的訊息。 這與控制流程模型中，使用控制結構，例如條件陳述式、 迴圈、 受管制的資料流量等等。

本文件提供如何使用訊息篩選條件的基本範例。 如需使用訊息篩選條件和資料流程模型來將訊息區連接的其他範例，請參閱[逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)並[逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

## <a name="example"></a>範例

請考慮下列函式， `count_primes`，其中說明不會篩選內送訊息的訊息區塊的基本使用方式。 訊息區塊將附加至的質數[std:: vector](../../standard-library/vector-class.md)物件。 `count_primes`函式會將數個數字傳送至訊息區塊、 訊息區塊，會收到的輸出值和列印至主控台的質數的這些數字。

[!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]

`transformer`物件處理所有輸入的值; 不過，它需要只是質數的值。 雖然可以撰寫應用程式，使訊息傳送者傳送只質數，但不能永遠知道訊息接收者的需求。

## <a name="example"></a>範例

下列函式中， `count_primes_filter`，會執行相同的工作`count_primes`函式。 不過，`transformer`物件在這個版本中的使用篩選函數來接受只是質數的值。 執行此動作的函式只會接收質數;因此，它沒有呼叫`is_prime`函式。

因為`transformer`物件會接收只質數，`transformer`物件本身可以保留質數。 亦即`transformer`不需要在此範例中的物件加入至質數`vector`物件。

[!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]

`transformer`物件現在會處理只是質數的值。 在上述範例中，`transformer`物件處理的所有訊息。 因此，上述範例必須收到它所傳送的訊息數目相同。 此範例中使用的結果[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式來判斷多少訊息，以接收來自`transformer`物件。 `send`函式會傳回 **，則為 true**訊息緩衝區時接受訊息並**false**當訊息緩衝區會拒絕訊息。 因此，訊息緩衝區會接受訊息的次數比對的質數的計數。

## <a name="example"></a>範例

下列程式碼顯示完整範例。 此範例會呼叫這兩`count_primes`函式和`count_primes_filter`函式。

[!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`primes-filter.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc 質數 filter.cpp**

## <a name="robust-programming"></a>穩固程式設計

篩選函式可以是 lambda 函式、 函式指標或函式物件。 每個篩選器函式會採用下列格式之一：

```Output
bool (T)
bool (T const &)
```

若要消除不必要的複製的資料，請在您傳輸之值的彙總類型時使用第二種形式。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[transformer 類別](../../parallel/concrt/reference/transformer-class.md)
