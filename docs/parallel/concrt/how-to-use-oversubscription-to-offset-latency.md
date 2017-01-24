---
title: "如何：使用過度訂閱使延遲產生位移 | Microsoft Docs"
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
  - "過度訂閱, 使用 [並行執行階段]"
  - "使用過度訂閱 [並行執行階段]"
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用過度訂閱使延遲產生位移
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

過度訂閱可以針對某些包含延遲性較高之工作的應用程式改善其整體效率。  本主題說明如何使用過度訂閱，緩解從網路連接讀取資料時所產生的延遲。  
  
## 範例  
 這個範例會使用[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)，從 HTTP 伺服器下載檔案。  `http_reader` 類別會衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 並且使用訊息傳遞，以非同步方式讀取要下載的 URL 名稱。  
  
 `http_reader` 類別會使用 [concurrency::task\_group](../Topic/task_group%20Class.md) 類別，以並行方式讀取每個檔案。  每項工作都會呼叫 [concurrency::Context::Oversubscribe](../Topic/Context::Oversubscribe%20Method.md) 方法並將 `_BeginOversubscription` 參數設定為 `true`，以便在目前的內容中啟用過度訂閱。  然後，每項工作都會使用 Microsoft Foundation Class \(MFC\) [CInternetSession](../../mfc/reference/cinternetsession-class.md) 和 [CHttpFile](../../mfc/reference/chttpfile-class.md) 類別來下載檔案。  最後，每項工作都會呼叫 `Context::Oversubscribe` 並將 `_BeginOversubscription` 參數設定為 `false`，以便停用過度訂閱。  
  
 啟用過度訂閱時，執行階段會建立一個用來執行工作的額外執行緒。  其中每個執行緒也可以過度訂閱目前的內容，因而建立額外的執行緒。  `http_reader` 類別會使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 物件來限制此應用程式所使用的執行緒數目。  此代理程式會使用固定數目的語彙基元值來初始化緩衝區。  針對每個下載作業，此代理程式會在作業啟動之前從緩衝區中讀取語彙基元值，然後在作業完成之後將此值重新寫入緩衝區。  當緩衝區是空的時，此代理程式就會等候其中一個下載作業將值重新寫入緩衝區。  
  
 下列範例會將同時工作的數目限制為可用硬體執行緒數目的兩倍。  當您實驗過度訂閱時，這個值是很好的起點。  您可以使用符合特定處理環境的值，也可以用動態方式變更此值，以便回應實際的工作負載。  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/CPP/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 這個範例會在配備四個處理器的電腦上產生下列輸出：  
  
  **http:\/\/www.adatum.com\/.. \(英文\) 下載**  
**http:\/\/www.adventure\-works.com\/.. \(英文\) 下載**  
**http:\/\/www.alpineskihouse.com\/.. \(英文\) 下載**  
**http:\/\/www.cpandl.com\/.. \(英文\) 下載**  
**http:\/\/www.cohovineyard.com\/.. \(英文\) 下載**  
**http:\/\/www.cohowinery.com\/.. \(英文\) 下載**  
**http:\/\/www.cohovineyardandwinery.com\/.. \(英文\) 下載**  
**http:\/\/www.contoso.com\/.. \(英文\) 下載**  
**http:\/\/www.consolidatedmessenger.com\/.. \(英文\) 下載**  
**http:\/\/www.fabrikam.com\/.. \(英文\) 下載**  
**http:\/\/www.fourthcoffee.com\/.. \(英文\) 下載**  
**http:\/\/www.graphicdesigninstitute.com\/.. \(英文\) 下載**  
**http:\/\/www.humongousinsurance.com\/.. \(英文\) 下載**  
**http:\/\/www.litwareinc.com\/.. \(英文\) 下載**  
**http:\/\/www.lucernepublishing.com\/.. \(英文\) 下載**  
**http:\/\/www.margiestravel.com\/.. \(英文\) 下載**  
**http:\/\/www.northwindtraders.com\/.. \(英文\) 下載**  
**http:\/\/www.proseware.com\/.. \(英文\) 下載**  
**http:\/\/www.fineartschool.net.. \(英文\) 下載**  
**http:\/\/www.tailspintoys.com\/.. \(英文\) 下載**  
**在 3276 毫秒下載 1801040 個位元組。** 啟用過度訂閱時，此範例的執行速度可能會更快，因為某些工作會執行，而其他工作則等候潛伏作業完成。  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `download-oversubscription.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列其中一個命令。  
  
 **cl.exe \/EHsc \/MD \/D "\_AFXDLL" download\-oversubscription.cpp**  
  
 **cl.exe \/EHsc \/MT download\-oversubscription.cpp**  
  
## 穩固程式設計  
 當您不再需要過度訂閱之後，請務必停用它。  假設有一個函式，但是它無法處理另一個函式所擲回的例外狀況。  如果您沒有在該函式傳回之前停用過度訂閱，任何其他平行工作也會過度訂閱目前的內容。  
  
 您可以使用「*資源擷取為初始設定*」\(Resource Acquisition Is Initialization，RAII\) 模式，將過度訂閱限制為指定的範圍。  在 RAII 模式下，資料結構會配置於堆疊上。  該資料結構會在建立時初始化或擷取資源，並在資料結構終結時終結或釋放該資源。  RAII 模式可保證在封閉範圍結束之前呼叫解構函式。  因此，當有例外狀況擲回或是函式包含多個 `return` 陳述式時，都會正確地管理資源。  
  
 下列範例會定義名為 `scoped_blocking_signal` 的結構。  `scoped_blocking_signal` 結構的建構函式會啟用過度訂閱，而解構函式則會停用過度訂閱。  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/CPP/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 下列範例會將 `download` 方法的主體修改成使用 RAII，以便確保函式傳回之前停用過度訂閱。  這項技術可確保 `download` 方法無例外狀況之虞。  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/CPP/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## 請參閱  
 [內容](../../parallel/concrt/contexts.md)   
 [Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)