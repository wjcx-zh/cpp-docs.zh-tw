---
title: "訊息傳遞函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9c2daa3f34ba4e73b28e11241d0f64680851fcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="message-passing-functions"></a>訊息傳遞函式
非同步代理程式程式庫提供幾個函式可讓您傳遞元件之間的訊息。  
  
 這些訊息傳遞函式會與不同的訊息區塊類型使用。 如需有關並行執行階段所定義的訊息區塊類型的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
##  <a name="top"></a> 章節  
 本主題描述下列的訊息傳遞函式：  
  
-   [傳送和 asend](#send)  
  
-   [接收和 try_receive](#receive)  
  
-   [範例](#examples)  
  
##  <a name="send"></a>傳送和 asend  

 [Concurrency:: send](reference/concurrency-namespace-functions.md#send)函式將訊息傳送至指定的目標以同步方式和[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式將訊息傳送至指定的目標以非同步的方式。 同時`send`和`asend`函式等候直到目標指出，它最終會接受或拒絕該訊息。  
  
 `send`函式會等候直到目標接受或拒絕該訊息，再傳回。 `send`函式會傳回`true`如果訊息已傳遞和`false`否則。 因為`send`函式以同步方式執行，`send`函式會等候接收訊息，再傳回目標。  
  
 相反地，`asend`函式不會等候目標接受或拒絕訊息，再傳回。 相反地，`asend`函式會傳回`true`如果目標接受該訊息，而且最終會將此。 否則，`asend`傳回`false`來指出目標拒絕該訊息或延後是否要使訊息的決策。  
  
 [[靠上](#top)]  
  
##  <a name="receive"></a>接收和 try_receive  

 [Concurrency:: receive](reference/concurrency-namespace-functions.md#receive)和[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)函式會從指定的來源讀取資料。 `receive`函式會等候資料變成可用，而`try_receive`函式會立即傳回。  
  
 使用`receive`函式時，您必須擁有資料以繼續執行。 使用`try_receive`函式必須不會封鎖目前的內容，或您沒有將資料以繼續執行。  
  
 [[靠上](#top)]  
  
##  <a name="examples"></a> 範例  
 如需範例，使用`send`和`asend`，和`receive`函式，請參閱下列主題：  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：實作各種生產者-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [如何：為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [如何：在已完成的工作之中選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 [[靠上](#top)]  
  
## <a name="see-also"></a>請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [send 函式](reference/concurrency-namespace-functions.md#send)   
 [asend 函式](reference/concurrency-namespace-functions.md#asend)   
 [接收函式](reference/concurrency-namespace-functions.md#receive)   
 [try_receive 函式](reference/concurrency-namespace-functions.md#try_receive)


