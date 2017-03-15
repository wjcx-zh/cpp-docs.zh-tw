---
title: "訊息傳遞函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息傳遞函式"
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
caps.latest.revision: 23
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息傳遞函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非同步代理程式程式庫提供數個可讓您在元件之間傳遞訊息的函式。  
  
 這些訊息傳遞函式可搭配各種不同的訊息區塊類型使用。  如需並行執行階段所定義之訊息區塊類型的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
##  <a name="top"></a> 章節  
 本主題說明下列訊息傳遞函式：  
  
-   [send 和 asend](#send)  
  
-   [receive 和 try\_receive](#receive)  
  
-   [範例](#examples)  
  
##  <a name="send"></a> send 和 asend  
 [concurrency::send](../Topic/send%20Function.md) 函式會以同步方式將訊息傳送至指定的目標，而 [concurrency::asend](../Topic/asend%20Function.md) 函式會以非同步方式將訊息傳送至指定的目標。  `send` 和 `asend` 函式都會等候目標表示終於接受或拒絕訊息。  
  
 `send` 函式會等到目標接受或拒絕訊息再傳回。  如果已傳遞訊息，則 `send` 函式會傳回 `true`，否則會傳回 `false`。  因為 `send` 函式是以同步方式運作，所以 `send` 函式會等到目標收到訊息再傳回。  
  
 相反地，`asend` 函式並不會等到目標接受或拒絕訊息才傳回。  如果目標接受訊息，而且最後會採用它，則 `asend` 函式會傳回 `true`。  否則，`asend` 會傳回 `false`，表示目標已拒絕訊息，或是以後才要決定是否採用訊息。  
  
 \[[上方](#top)\]  
  
##  <a name="receive"></a> receive 和 try\_receive  
 [concurrency::receive](../Topic/receive%20Function.md) 和 [concurrency::try\_receive](../Topic/try_receive%20Function.md) 函式會從指定的來源讀取資料。  `receive` 函式會等到有資料可用時才傳回，而 `try_receive` 函式則會立即傳回。  
  
 當您必須要有資料才能繼續時，請使用 `receive` 函式。  如果您絕對不能封鎖目前的內容，或是沒有資料也可以繼續，請使用 `try_receive` 函式。  
  
 \[[上方](#top)\]  
  
##  <a name="examples"></a> 範例  
 如需使用 `send`、`asend` 和 `receive` 函式的範例，請參閱下列主題：  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [如何：實作各種生產者\-消費者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [如何：為呼叫和轉換程式類別提供工作函式](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [如何：在資料管線中使用轉換程式](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [如何：在已完成的工作之中選取](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [如何：定期傳送訊息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [如何：使用訊息區篩選條件](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 \[[上方](#top)\]  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [send 函式](../Topic/send%20Function.md)   
 [asend 函式](../Topic/asend%20Function.md)   
 [receive 函式](../Topic/receive%20Function.md)   
 [try\_receive 函式](../Topic/try_receive%20Function.md)