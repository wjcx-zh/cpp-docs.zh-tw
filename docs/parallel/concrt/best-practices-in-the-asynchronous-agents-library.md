---
title: "非同步代理程式程式庫中的最佳做法 | Microsoft Docs"
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
  - "最佳做法, 非同步代理程式程式庫"
  - "非同步代理程式程式庫, 最佳做法"
  - "非同步代理程式程式庫, 要避免的做法"
  - "要避免的做法, 非同步代理程式程式庫"
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 非同步代理程式程式庫中的最佳做法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件說明非同步代理程式程式庫的有效用法。  代理程式程式庫可提升以行動為基礎的程式撰寫模型，以及針對粗略資料流程和管線工作的同處理序訊息傳遞。  
  
 如需代理程式程式庫的詳細資訊，請參閱[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)。  
  
##  <a name="top"></a> 章節  
 本文件包括下列章節：  
  
-   [使用代理程式隔離狀態](#isolation)  
  
-   [使用節流機制來限制資料管線中的訊息數目](#throttling)  
  
-   [不要在資料管線中執行精細工作](#fine-grained)  
  
-   [不要以傳值方式傳遞大型訊息裝載](#large-payloads)  
  
-   [當擁有權未定義時，在資料網路中使用 shared\_ptr](#ownership)  
  
##  <a name="isolation"></a> 使用代理程式隔離狀態  
 代理程式程式庫可讓您透過非同步訊息傳遞機制來連接隔離的元件，以共用狀態以外的形式作業。  非同步代理程式在將其內部狀態與其他元件隔離時最有效。  藉由隔離狀態，多個元件通常不會作用於共用資料。  狀態隔離可讓您的應用程式延展，因為它會減少共用記憶體爭用。  狀態隔離也會減少死結和競爭條件的機率，因為元件不必同步處理對共用資料的存取。  
  
 您通常藉由將資料成員保存在代理程式類別的 `private` 或 `protected` 區段中，或藉由使用訊息緩衝區溝通狀態變更，在代理程式中隔離狀態。  下列範例示範衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 類別的 `basic_agent` 類別。  `basic_agent` 類別使用兩個訊息緩衝區，與外部元件通訊。  一個訊息緩衝區保存傳入訊息，另一個訊息緩衝區則保存外寄訊息。  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 如需如何定義及使用代理程式的完整範例，請參閱[逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="throttling"></a> 使用節流機制來限制資料管線中的訊息數目  
 許多訊息緩衝區類型 \(例如 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md)\) 都會保存不限數目的訊息。  當訊息生產者傳送訊息至資料管線的速度比消費者處理這些速度更快時，應用程式可能會進入記憶體不足或記憶體用完狀態。  您可以使用節流機制 \(例如信號\)，限制資料管線中同時使用的訊息數目。  
  
 在下列基本範例中，會示範如何使用信號來限制資料管線中的訊息數目。  資料管線使用 [concurrency::wait](../Topic/wait%20Function.md) 函式，模擬所需時間至少為 100 毫秒的作業。  因為傳送者產生訊息的速度比消費者處理這些訊息更快，所以這個範例定義了 `semaphore` 類別，讓應用程式限制使用中訊息的數目。  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore` 物件會限制管線每次最多處理兩則訊息。  
  
 在這個範例中，生產者會將相當少的訊息傳送給消費者。  因此，這個範例不會示範潛在的記憶體不足或記憶體用完狀況。  不過，當資料管線包含相當大量的訊息時，這個機制很實用。  
  
 如需如何建立這個範例中所用信號類別的詳細資訊，請參閱 [如何：使用內容類別實作合作式信號](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="fine-grained"></a> 不要在資料管線中執行精細工作  
 當資料管線所執行的工作相當粗略時，代理程式程式庫最實用。  例如，某個應用程式元件可能從檔案或網路連接中讀取資料，並偶爾將該資料傳送至另一個元件。  代理程式程式庫用來傳播訊息的通訊協定會導致訊息傳遞機制的額外負荷大於[平行模式程式庫](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\) 所提供的工作平行建構。  因此，請確定資料管線所執行的工作所需時間夠長，足以抵銷此額外負荷。  
  
 雖然資料管線在其工作是粗略時最有效，但資料管線的每個階段都可以使用 PPL 建構，例如工作群組和平行演算法，來執行更精細的工作。  如需在每個處理階段使用精細平行處理原則之粗略資料網路的範例，請參閱[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 \[[上方](#top)\]  
  
##  <a name="large-payloads"></a> 不要以傳值方式傳遞大型訊息裝載  
 在某些情況下，執行階段會針對它從某個訊息緩衝區傳遞至另一個訊息緩衝區的每則訊息建立複本。  例如，[concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 類別會針對它所收到的每則訊息，將複本提供給每個目標。  當您使用訊息傳遞函式，例如 [concurrency::send](../Topic/send%20Function.md) 和 [concurrency::receive](../Topic/receive%20Function.md)，對訊息緩衝區寫入訊息及讀取訊息時，執行階段也會建立訊息資料的複本。  雖然這個機制有助於排除同時寫入共用資料的風險，但是當訊息裝載相當大時，它可能會導致記憶體效能降低。  
  
 當您傳遞大型裝載的訊息時，可以使用指標或參考改善記憶體效能。  下列範例比較兩種作法：以傳值方式傳遞大型訊息，以及傳遞相同訊息類型的指標。  範例定義兩個作用於 `message_data` 物件的代理程式類型 `producer` 和 `consumer`。  範例比較生產者傳遞數個 `message_data` 物件至消費者的所需時間與生產者代理程式傳送數個 `message_data` 物件指標至消費者的所需時間。  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出：  
  
  **使用 message\_data…**  
**採用了 437ms。**  
**使用 message\_data\*…**  
**採用了 47ms。** 使用指標的版本效能較佳，因為它不需要執行階段針對它從生產者傳遞至消費者的每個 `message_data` 物件建立完整複本。  
  
 \[[上方](#top)\]  
  
##  <a name="ownership"></a> 當擁有權未定義時，在資料網路中使用 shared\_ptr  
 當您透過訊息傳遞管線或網路以指標方式傳送訊息時，通常會在網路前端配置每則訊息的記憶體，而在網路末端釋放該記憶體。  雖然這個機制通常運作良好，但在某些情況下難以使用或無法使用。  例如，當資料網路包含多個結束節點的情況。  在此情況下，沒有清楚位置可釋放訊息的記憶體。  
  
 若要解決此問題，您可以使用讓多個元件擁有一個指標的機制，例如 [std::shared\_ptr](../../standard-library/shared-ptr-class.md)。  當擁有資源的最終 `shared_ptr` 物件終結時，同時也會釋放資源。  
  
 下列範例示範如何使用 `shared_ptr`，在多個訊息緩衝區之間共用指標值。  範例將 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 物件連接至三個 [concurrency::call](../../parallel/concrt/reference/call-class.md) 物件。  `overwrite_buffer` 類別會將訊息提供給每個目標。  因為在資料網路末端有多個資料擁有者，所以這個範例使用 `shared_ptr` 讓每個 `call` 物件共用訊息擁有權。  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出：  
  
  **建立資源 42...**  
**receiver1:接收的資源 42**  
**建立資源 64...**  
**receiver2:接收的資源 42**  
**receiver1: 接收的資源 64**  
**要終結的資源 42…**  
**receiver2: 接收的資源 64**  
**要終結的資源 64…**   
## 請參閱  
 [並行執行階段最佳作法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [逐步解說：建立資料流程代理程式](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [平行模式程式庫中的最佳作法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [並行執行階段中的一般最佳作法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)