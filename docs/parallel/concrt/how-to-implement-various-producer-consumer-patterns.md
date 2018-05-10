---
title: 如何： 實作各種生產者-消費者模式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50a6683db37fb6e994c1957a8df3ab6469acff6d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>如何：實作各種生產者-消費者模式
本主題描述如何在您的應用程式中實作生產者-消費者模式。 在此模式中，「生產者」會將訊息傳送至訊息區塊，而「消費者」會從該區塊讀取訊息。  
  
 本主題會示範兩種案例。 在第一個案例中，取用者必須接收每則的生產者傳送訊息。 在第二個案例中，取用者會定期輪詢資料，並因此不需要接收每則訊息。  
  
 本主題中的這兩個範例會使用代理程式、 訊息區塊與訊息傳遞函式來傳輸訊息產生者從取用者。 產生者代理程式會使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式來寫入訊息至[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)物件。 取用者代理程式會使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函式來讀取訊息[concurrency:: isource](../../parallel/concrt/reference/isource-class.md)物件。 這兩個代理程式會保存協調處理結尾之 sentinel 值。  
  
 如需非同步代理程式的詳細資訊，請參閱[非同步代理程式](../../parallel/concrt/asynchronous-agents.md)。 如需訊息區和訊息傳遞函式的詳細資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)和[訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)。  
  
## <a name="example"></a>範例  
 在此範例中，產生者代理程式會將一連串數字傳送至取用者代理程式。 取用者會收到每個這些數字，並計算其平均值。 應用程式會寫入主控台中的平均值。  
  
 這個範例會使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)物件來啟用佇列訊息產生者。 `unbounded_buffer`類別會實作`ITarget`和`ISource`使生產者和取用者可以傳送和接收訊息的共用緩衝區。 `send`和`receive`函式協調工作傳播產生者將取用者的資料。  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
The average is 50.  
```  
  
## <a name="example"></a>範例  
 在此範例中，產生者代理程式會將一系列的股票報價傳送至取用者代理程式。 取用者代理程式會定期讀取目前的引號，並列印到主控台。  
  
 這個範例類似於上一個，不同之處在於它會使用[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)物件，讓產生者與取用者共用一個訊息。 如同先前的範例，`overwrite_buffer`類別會實作`ITarget`和`ISource`，讓產生者和消費者可以共用的訊息的緩衝區上執行。  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 這個範例會產生下列輸出範例。  
  
```Output  
Current quote is 24.44.  
Current quote is 24.44.  
Current quote is 24.65.  
Current quote is 24.99.  
Current quote is 23.76.  
Current quote is 22.30.  
Current quote is 25.89.  
```  
  
 不同於與`unbounded_buffer`物件`receive`函式不會移除從訊息`overwrite_buffer`物件。 如果取用者讀取自訊息緩衝區超過一次之前產生者會覆寫該訊息，接收者會取得相同的訊息每次。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`producer-consumer.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc 生產者 consumer.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)
