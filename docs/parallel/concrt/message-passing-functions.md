---
title: 訊息傳遞函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7435bdbc4d5959771a1f80e2ad12f038a8157bae
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162278"
---
# <a name="message-passing-functions"></a>訊息傳遞函式

非同步代理程式程式庫提供數個函數可讓您傳遞元件之間的訊息。

這些訊息傳遞函式可搭配各種訊息區塊類型。 如需並行執行階段所定義的訊息區塊類型的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。

##  <a name="top"></a> 章節

本主題描述下列的訊息傳遞函式：

- [傳送和 asend](#send)

- [接收及 try_receive](#receive)

- [範例](#examples)

##  <a name="send"></a> 傳送和 asend

[Concurrency:: send](reference/concurrency-namespace-functions.md#send)函式將訊息傳送至指定的目標以同步方式並[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式將訊息傳送至指定的目標以非同步的方式。 同時`send`和`asend`函式等候，直到目標表示，它最終會接受或拒絕該訊息。

`send`函式會等候直到目標接受或拒絕訊息，再傳回。 `send`函式會傳回 **，則為 true**如果訊息已傳遞並**false**否則。 因為`send`函式以同步方式執行，`send`函式會等待接收訊息之前它會傳回, 目標。

相反地，`asend`函式不會等候目標接受或拒絕訊息，再傳回。 相反地，`asend`函式會傳回 **，則為 true**如果目標接受訊息，並最終將會需要它。 否則，請`asend`會傳回**false**來指出目標拒絕訊息或延後決定是否要接收的訊息。

[[靠上](#top)]

##  <a name="receive"></a> 接收及 try_receive

[Concurrency:: receive](reference/concurrency-namespace-functions.md#receive)並[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)函式會讀取指定之來源中的資料。 `receive`函式會等待資料變成可用，而`try_receive`函式會立即傳回。

使用`receive`函式時，您必須擁有要繼續的資料。 使用`try_receive`函式必須不會封鎖目前的內容，或您沒有已繼續的資料。

[[靠上](#top)]

##  <a name="examples"></a> 範例

如需範例，使用`send`並`asend`，和`receive`函式，請參閱下列主題：

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
[接收函式](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 函式](reference/concurrency-namespace-functions.md#try_receive)

