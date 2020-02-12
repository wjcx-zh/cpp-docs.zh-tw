---
title: 如何：定期傳送訊息
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142468"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：定期傳送訊息

這個範例示範如何使用 concurrency：：[timer 類別](../../parallel/concrt/reference/timer-class.md)定期傳送訊息。

## <a name="example"></a>範例

下列範例會使用 `timer` 物件來報告長時間作業期間的進度。 這個範例會將 `timer` 物件連結至[concurrency：： call](../../parallel/concrt/reference/call-class.md)物件。 `call` 物件會定期將進度指示器列印到主控台。 [Concurrency：： timer：： start](reference/timer-class.md#start)方法會在不同的內容上執行計時器。 `perform_lengthy_operation` 函式會呼叫主要內容上的[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函式，以模擬耗時的作業。

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

這個範例會產生下列範例輸出：

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼入 Visual Studio 專案中，或貼入名為 `report-progress.cpp` 的檔案中，然後在 [Visual Studio 命令提示字元] 視窗中執行下列命令。

> **cl/EHsc report-progress.cpp .cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
