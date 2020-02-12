---
title: 訊息傳遞函式
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143290"
---
# <a name="message-passing-functions"></a>訊息傳遞函式

非同步代理程式程式庫提供數個函數，可讓您在元件之間傳遞訊息。

這些訊息傳遞函式會搭配各種訊息區塊類型使用。 如需並行執行階段所定義之訊息區塊類型的詳細資訊，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="top"></a> 章節

本主題描述下列訊息傳遞函式：

- [傳送和 asend](#send)

- [接收和 try_receive](#receive)

- [範例](#examples)

## <a name="send"></a>傳送和 asend

[Concurrency：： send](reference/concurrency-namespace-functions.md#send)函式會以同步方式將訊息傳送至指定的目標，而[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函式會以非同步方式將訊息傳送至指定的目標。 `send` 和 `asend` 函式都會等到目標指出它最後會接受或拒絕訊息。

`send` 函式會等候直到目標接受或拒絕訊息傳回為止。 如果傳遞訊息，`send` 函數會傳回**true** ，否則傳回**false** 。 因為 `send` 函式會以同步方式運作，所以 `send` 函式會等候目標接收訊息，然後再傳回。

相反地，`asend` 函式不會等待目標在傳回之前接受或拒絕訊息。 相反地，如果目標接受訊息，且最後將會採用它，則 `asend` 函數會傳回**true** 。 否則，`asend` 會傳回**false** ，表示目標已拒絕訊息，或已延遲有關是否要接受訊息的決策。

[[靠上](#top)]

## <a name="receive"></a>接收和 try_receive

[Concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和[concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)函式會從指定的來源讀取資料。 `receive` 函式會等候資料變成可用，而 `try_receive` 函數則會立即傳回。

當您必須要有資料才能繼續時，請使用 `receive` 函數。 如果您不能封鎖目前的內容，或是不需要讓資料繼續進行，請使用 `try_receive` 函數。

[[靠上](#top)]

## <a name="examples"></a> 範例

如需使用 `send` 和 `asend`，以及 `receive` 函式的範例，請參閱下列主題：

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [如何：為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [如何：在已完成的工作之中選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 函式](reference/concurrency-namespace-functions.md#send)<br/>
[asend 函式](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 函式](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函式](reference/concurrency-namespace-functions.md#try_receive)
