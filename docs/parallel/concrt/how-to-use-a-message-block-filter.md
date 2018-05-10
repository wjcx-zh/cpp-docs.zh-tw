---
title: 如何： 使用訊息區篩選條件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92de322142e56eb9907da2e19d350c3af9c8a7d9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-a-message-block-filter"></a>如何：使用訊息區篩選條件
本文件將示範如何使用篩選函數，以啟用非同步化訊息區塊接受或拒絕該訊息的裝載根據訊息。  
  
 當您建立訊息區塊物件例如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)、 [concurrency:: call](../../parallel/concrt/reference/call-class.md)，或[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)，您可以提供*filter 函數*，判斷訊息區塊接受或拒絕訊息。 篩選函數是有用的方式，若要保證的訊息區塊只接收特定值。  
  
 篩選函數很重要，因為它們可讓您連接訊息區塊組成*資料流程網路*。 在資料流程網路中，訊息區塊控制的資料流程處理僅符合特定準則的訊息。 控制流程模型，其中的資料流程會藉由使用控制結構，例如條件陳述式，迴圈，調節相比較，並以此類推。  
  
 本文件提供如何使用訊息篩選條件的基本範例。 使用訊息篩選條件和資料流程模型連線訊息區塊的其他範例，請參閱[逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)和[逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
## <a name="example"></a>範例  
 請考慮下列函式`count_primes`，其中說明基本的使用方式，不會篩選內送訊息的訊息區塊。 訊息區塊將附加至質數[std:: vector](../../standard-library/vector-class.md)物件。 `count_primes`函式會將多個編號傳送至訊息區塊、 接收之訊息區塊的輸出值和列印到主控台的質數這些數字。  
  
 [!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]  
  
 `transformer`物件處理所有輸入的值，不過，必須只是質數的值。 雖然無法撰寫應用程式，使訊息傳送者傳送質數數字，但無法一律呈現已知訊息接收者的需求。  
  
## <a name="example"></a>範例  
 下列函式`count_primes_filter`，執行相同的工作當做`count_primes`函式。 不過，`transformer`在此版本中的物件可用於篩選函數僅接受這些值屬於質數。 執行此動作的函式只會接收質數。因此，它沒有呼叫`is_prime`函式。  
  
 因為`transformer`物件接收質數數字，`transformer`物件本身可以保留質數。 換句話說，`transformer`不需要在此範例中的物件加入至質數`vector`物件。  
  
 [!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]  
  
 `transformer`物件現在會處理屬於質數這些值。 在上述範例中，`transformer`物件處理的所有訊息。 因此前, 一個範例必須收到相同的傳送的訊息數目。 此範例中使用的結果[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式來判斷多少訊息，以接收來自`transformer`物件。 `send`函式會傳回`true`訊息緩衝區時接受該訊息和`false`當訊息緩衝區會拒絕訊息。 因此，訊息緩衝區會接受該訊息的次數比對的質數的計數。  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整範例。 此範例會呼叫兩者`count_primes`函式和`count_primes_filter`函式。  
  
 [!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`primes-filter.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc primes filter.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 篩選函數可以是 lambda 函式、 函式指標或函式物件。 每個篩選函數會採用下列格式之一：  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 若要消除不必要的複製的資料，請使用第二種形式，如果傳輸之值的彙總類型。  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [逐步解說： 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [逐步解說： 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [transformer 類別](../../parallel/concrt/reference/transformer-class.md)
