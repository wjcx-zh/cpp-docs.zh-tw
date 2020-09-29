---
title: 如何：實作各種生產者-消費者模式
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 70813adf6715a2bcaf4af7370ce43d99c44263bd
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413771"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>如何：實作各種生產者-消費者模式

本主題說明如何在您的應用程式中執行生產者-取用者模式。 在此模式中，「生產者」** 會將訊息傳送至訊息區塊，而「消費者」** 會從該區塊讀取訊息。

本主題會示範兩個案例。 在第一個案例中，取用者必須接收生產者傳送的每則訊息。 在第二個案例中，取用者會定期輪詢資料，因此不需要接收每個訊息。

本主題中的兩個範例都會使用代理程式、訊息區塊和訊息傳遞函式，將訊息從生產者傳送到取用者。 生產者代理程式使用 [concurrency：： send](reference/concurrency-namespace-functions.md#send) 函式將訊息寫入 [Concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md) 物件。 取用者代理程式使用 [concurrency：： receive](reference/concurrency-namespace-functions.md#receive) 函式來讀取 [Concurrency：： ISource](../../parallel/concrt/reference/isource-class.md) 物件的訊息。 這兩個代理程式都會保存 sentinel 值，以協調處理結束。

如需非同步代理程式的詳細資訊，請參閱 [非同步代理](../../parallel/concrt/asynchronous-agents.md)程式。 如需有關訊息區塊和訊息傳遞函式的詳細資訊，請參閱 [非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md) 和 [訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)。

## <a name="example-send-series-of-numbers-to-consumer-agent"></a>範例：將一連串的數位傳送給取用者代理程式

在此範例中，生產者代理程式會將一連串的數位傳送給取用者代理程式。 取用者會收到每個數位，並計算其平均值。 應用程式會將平均寫入主控台。

這個範例會使用 [concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md) 物件，讓生產者能夠將訊息排入佇列。 `unbounded_buffer`類別會執行 `ITarget` ， `ISource` 讓生產者和取用者可以在共用緩衝區之間傳送和接收訊息。 和函式會 `send` `receive` 協調將資料從生產者傳播至取用者的工作。

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

此範例會產生下列輸出。

```Output
The average is 50.
```

## <a name="example-send-series-of-stock-quotes-to-consumer-agent"></a>範例：將股票報價系列傳送給取用者代理程式

在此範例中，生產者代理程式會將一系列股票報價傳送給取用者代理程式。 取用者代理程式會定期讀取目前的報價，並將其列印至主控台。

這個範例與上一個範例類似，不同之處在于它會使用 [concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 物件，讓生產者與取用者共用一則訊息。 如先前的範例所示， `overwrite_buffer` 類別 `ITarget` 會執行， `ISource` 讓生產者和取用者可以在共用的訊息緩衝區上採取動作。

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

此範例會產生下列範例輸出。

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

與物件不同的是，函式不 `unbounded_buffer` `receive` 會從物件中移除訊息 `overwrite_buffer` 。 如果取用者在生產者覆寫該訊息之前，多次讀取訊息緩衝區，接收者會每次都取得相同的訊息。

## <a name="compiling-the-code"></a>編譯程式碼

請複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為的檔案中， `producer-consumer.cpp` 然後在 Visual Studio 命令提示字元視窗中執行下列命令。

**cl.exe/EHsc producer-consumer .cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
