---
title: 如何： 定期傳送訊息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3c476d9cf633ce9b676dc8f658c94bd0b240461
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384288"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>如何：定期傳送訊息

此範例示範如何使用並行存取::[timer 類別](../../parallel/concrt/reference/timer-class.md)定期傳送訊息。

## <a name="example"></a>範例

下列範例會使用`timer`長時間作業期間報告進度的物件。 此範例的連結`timer`物件至[concurrency:: call](../../parallel/concrt/reference/call-class.md)物件。 `call`物件定期列印至主控台的進度列指示器。 [Concurrency::timer::start](reference/timer-class.md#start)方法會在個別的內容中的計時器。 `perform_lengthy_operation`函式會呼叫[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函式來模擬耗時的作業在主要內容。

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

此範例會產生下列的範例輸出：

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>編譯程式碼

複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼入名為的檔案中`report-progress.cpp`，然後在 Visual Studio 命令提示字元 視窗中執行下列命令。

**cl.exe /EHsc report-progress.cpp**

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
