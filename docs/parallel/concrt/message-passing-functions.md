---
title: 訊息傳遞函式
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 3709e7b5280b96b2b77ec850a06ed15d0e42a7e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194624"
---
# <a name="message-passing-functions"></a>訊息傳遞函式

非同步代理程式程式庫提供數個函數，可讓您在元件之間傳遞訊息。

這些訊息傳遞函式會搭配各種訊息區塊類型使用。 如需並行執行階段所定義之訊息區塊類型的詳細資訊，請參閱[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="sections"></a><a name="top"></a>各節

本主題描述下列訊息傳遞函式：

- [傳送和 asend](#send)

- [接收和 try_receive](#receive)

- [範例](#examples)

## <a name="send-and-asend"></a><a name="send"></a>傳送和 asend

[Concurrency：： send](reference/concurrency-namespace-functions.md#send)函式會以同步方式將訊息傳送至指定的目標，而[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函式會以非同步方式將訊息傳送至指定的目標。 和函式都會 `send` `asend` 等到目標指出它最後會接受或拒絕訊息。

函式 `send` 會等候，直到目標接受或拒絕訊息傳回為止。 `send` **`true`** 如果訊息已傳遞，此函式會傳回，否則會傳回 **`false`** 。 因為函式會 `send` 以同步方式運作，所以函式會 `send` 先等候目標接收訊息，然後再傳回。

相反地，函式不會在傳回 `asend` 之前等待目標接受或拒絕訊息。 相反地， `asend` **`true`** 如果目標接受訊息，而且最終會採用它，則函式會傳回。 否則，會傳回 `asend` **`false`** 以表示目標已拒絕訊息，或已延遲有關是否要接受訊息的決策。

[[頂端](#top)]

## <a name="receive-and-try_receive"></a><a name="receive"></a>接收和 try_receive

[Concurrency：： receive](reference/concurrency-namespace-functions.md#receive)和[concurrency：： try_receive](reference/concurrency-namespace-functions.md#try_receive)函式會從指定的來源讀取資料。 函式 `receive` 會等候資料變成可用，而函式會 `try_receive` 立即傳回。

`receive`當您必須要有資料才能繼續時，請使用函數。 `try_receive`如果您不能封鎖目前的內容，或是不需要讓資料繼續進行，請使用函數。

[[頂端](#top)]

## <a name="examples"></a><a name="examples"></a> 範例

如需使用和、和函式的範例， `send` `asend` `receive` 請參閱下列主題：

- [非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)

- [如何：執行各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [如何：將工作函式提供給呼叫和轉換器類別](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [如何：在資料管線中使用轉換器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [如何：在已完成的工作中進行選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [如何：使用訊息區篩選器](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[頂端](#top)]

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區塊](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 函式](reference/concurrency-namespace-functions.md#send)<br/>
[asend 函式](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 函式](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函式](reference/concurrency-namespace-functions.md#try_receive)
