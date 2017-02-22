---
title: "如何：使用訊息區篩選條件 | Microsoft Docs"
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
  - "訊息區篩選，使用 [並行執行階段]"
  - "使用訊息區篩選 [並行執行階段]"
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：使用訊息區篩選條件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件將示範如何使用篩選器函式，讓非同步訊息區塊接受或拒絕以該訊息的內容為基礎的訊息。  
  
 當您建立訊息區塊物件如 [unbounded_buffer](../Topic/unbounded_buffer%20Class.md), 、 [concurrency:: call](../../parallel/concrt/reference/call-class.md), ，或 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md), ，您可以提供 *filter 函數* ，判斷訊息區塊接受或拒絕訊息。 Filter 函式是保證的訊息區塊只接收特定值的實用方式。  
  
 篩選函數很重要，因為它們可讓您連接訊息區塊組成 *資料流程網路*。 在資料流程網路中，訊息區塊控制資料的流量處理只有在符合特定準則的訊息。 控制流程模型，其中的資料流程藉由使用控制結構，例如條件陳述式、 迴圈、 調節相比較，並以此類推。  
  
 本文件提供如何使用訊息篩選條件的基本範例。 使用訊息篩選條件和資料流程模型來將訊息區連接的其他範例，請參閱 [逐步解說︰ 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) 和 [逐步解說︰ 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
## <a name="example"></a>範例  
 請考慮下列函式， `count_primes`, ，其中說明基本的使用方式，不會篩選內送訊息的訊息區塊。 訊息區塊附加至質數 [std:: vector](../../standard-library/vector-class.md) 物件。  `count_primes` 函式訊息區塊傳送多個編號、 訊息區塊中，從接收的輸出值和列印到主控台的質數的這些數字。  
  
 [!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/CPP/how-to-use-a-message-block-filter_1.cpp)]  
  
  `transformer` 處理所有輸入的值的物件; 不過，它需要只是質數的值。 雖然可以撰寫應用程式，使訊息傳送者將只質數，永遠無法知道訊息接收者的需求。  
  
## <a name="example"></a>範例  
 下列函式， `count_primes_filter`, ，會執行相同的工作 `count_primes` 函式。 不過， `transformer` 物件在這個版本中的使用篩選器函式接受只是質數的值。 執行動作的函式只會收到質數。因此，它並沒有呼叫 `is_prime` 函式。  
  
 因為 `transformer` 物件接收只質數， `transformer` 物件本身可以保留質數。 換句話說， `transformer` 不需要在此範例中的物件加入至質數 `vector` 物件。  
  
 [!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/CPP/how-to-use-a-message-block-filter_2.cpp)]  
  
  `transformer` 物件現在處理只是質數的值。 在上述範例中， `transformer` 物件處理所有訊息。 因此，上述範例必須接收相同的傳送的訊息數目。 此範例中使用的結果 [concurrency:: send](../Topic/send%20Function.md) 函式來判斷從接收的訊息數目 `transformer` 物件。  `send` 函式會傳回 `true` 訊息緩衝區時接受的訊息和 `false` 訊息緩衝區時就會拒絕訊息。 因此，訊息緩衝區接受訊息的次數比對質數的計數。  
  
## <a name="example"></a>範例  
 下列程式碼顯示完整範例。 此範例會呼叫兩者 `count_primes` 函式和 `count_primes_filter` 函式。  
  
 [!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/CPP/how-to-use-a-message-block-filter_3.cpp)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼並將它貼在 Visual Studio 專案中，或貼入名為的檔案 `primes-filter.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc 質數 filter.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 Filter 函式可以是 lambda 函式、 函式指標或函式物件。 每個篩選條件的函式會採用下列格式之一︰  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 若要消除不必要的複製的資料，使用第二個表單時已傳輸之值的彙總類型。  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [逐步解說︰ 建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [逐步解說︰ 建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [transformer 類別](../../parallel/concrt/reference/transformer-class.md)
