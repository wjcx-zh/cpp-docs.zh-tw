---
title: "如何：實作各種生產者-消費者模式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生產者-消費者模式, 實作 [並行執行階段]"
  - "實作生產者-消費者模式 [並行執行階段]"
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：實作各種生產者-消費者模式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何在您的應用程式中實作生產者\-消費者模式。  在這個模式中，「*生產者*」\(Producer\) 會傳送訊息至訊息區塊，而「*消費者*」\(Consumer\) 則會從該區塊讀取訊息。  
  
 本主題會示範兩個情境。  在第一個情境中，消費者必須收到產生者所傳送的每個訊息。  在第二個情境中，消費者會定期輪詢資料，因此不需要收到每個訊息。  
  
 本主題中的兩個範例都會使用代理程式、訊息區塊和訊息傳遞函式，將訊息從生產者傳輸給消費者。  生產者代理程式會使用 [concurrency::send](../Topic/send%20Function.md) 函式將訊息寫入至 [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) 物件。  消費者代理程式會使用 [concurrency::receive](../Topic/receive%20Function.md) 函式從 [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) 物件讀取訊息。  這兩個代理程式都保有 Sentinel 值，以協調處理結束。  
  
 如需非同步代理程式的詳細資訊，請參閱[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)。  如需訊息區塊和訊息傳遞函式的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)和[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)。  
  
## 範例  
 在這個範例中，生產者代理程式會將一系列的數字傳送給消費者代理程式。  消費者在收到所有這些數字之後，會計算它們的平均值。  應用程式會將平均值寫入主控台。  
  
 這個範例會使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 物件，讓生產者將訊息放入佇列中。  `unbounded_buffer` 類別會實作 `ITarget` 和 `ISource`，讓生產者和消費者可以在共用緩衝區中傳送與接收訊息。  `send` 和 `receive` 函式會協調將資料從生產者傳播給消費者的工作。  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 這個範例產生下列輸出。  
  
  **平均值為 50。**   
## 範例  
 在這個範例中，生產者代理程式會將一系列的股價傳送給消費者代理程式。  消費者代理程式會定期讀取目前的報價，並將它列印至主控台。  
  
 這個範例與前一個範例類似，不同之處在於它是使用 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 物件讓生產者將某個訊息與消費者共用。  與前一個範例相同，`overwrite_buffer` 類別會實作 `ITarget` 和 `ISource`，讓生產者和消費者可以對共用訊息緩衝區執行動作。  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 這個範例 \(Example\) 產生下列範例 \(Sample\) 輸出。  
  
  **目前的值是 24.44。**  
**目前的值是 24.44。**  
**目前的值是 24.65。**  
**目前的值是 24.99。**  
**目前的值是 23.76。**  
**目前的值是 22.30。**  
**目前的值是 25.89。** 與使用 `unbounded_buffer` 物件時不同，`receive` 函式並不會從 `overwrite_buffer` 物件移除訊息。  如果消費者在生產者覆寫該訊息之前多次讀取訊息緩衝區，則消費者每次都會得到相同的訊息。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `producer-consumer.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc producer\-consumer.cpp**  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)