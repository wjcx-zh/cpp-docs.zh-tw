---
title: "如何： 使用過度訂閱位移延遲 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1a8f059abffd261de2002ed5d18067c48d74876
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>如何：使用過度訂閱使延遲產生位移
過度訂閱可以改善整體效率的某些應用程式會包含具有大量的延遲的工作。 本主題說明如何使用過度訂閱位移的延遲所造成的網路連線讀取資料。  
  
## <a name="example"></a>範例  
 這個範例會使用[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)從 HTTP 伺服器下載檔案。 `http_reader`類別衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)和使用訊息傳遞，以非同步方式讀取要下載的 URL 名稱。  
  
 `http_reader`類別會使用[concurrency:: task_group](reference/task-group-class.md)類別以並行方式讀取每個檔案。 每個工作都會呼叫[concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe)方法`_BeginOversubscription`參數設定為`true`啟用過度訂閱目前內容中的。 每項工作接著會使用 Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md)和[Cinternetfile](../../mfc/reference/chttpfile-class.md)類別，以下載檔案。 最後，每個工作都會呼叫`Context::Oversubscribe`與`_BeginOversubscription`參數設定為`false`停用過度訂閱。  
  
 啟用過度訂閱時，執行階段會建立一個額外的執行緒，用來執行工作。 每個執行緒可以也過度訂閱目前內容，並藉此建立額外的執行緒。 `http_reader`類別會使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)物件來限制應用程式所使用的執行緒數目。 代理程式初始化具有固定數目的語彙基元值的緩衝區。 每個下載作業，代理程式會從緩衝區讀取語彙基元值之前作業啟動，然後將該值傳回寫入緩衝區在作業完成之後。 緩衝區是空的當代理程式會等候下載作業回寫至緩衝區的值之一。  
  
 下列範例會限制同時工作兩次的數字的可用硬體執行緒數目。 這個值會是很好的起點時嘗試使用過度訂閱使用。 您可以使用符合特定的處理環境的值，或以動態方式變更此值可回應的實際工作負載。  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 這個範例會產生具有四個處理器的電腦上的下列輸出：  
  
```Output  
Downloading http://www.adatum.com/...  
Downloading http://www.adventure-works.com/...  
Downloading http://www.alpineskihouse.com/...  
Downloading http://www.cpandl.com/...  
Downloading http://www.cohovineyard.com/...  
Downloading http://www.cohowinery.com/...  
Downloading http://www.cohovineyardandwinery.com/...  
Downloading http://www.contoso.com/...  
Downloading http://www.consolidatedmessenger.com/...  
Downloading http://www.fabrikam.com/...  
Downloading http://www.fourthcoffee.com/...  
Downloading http://www.graphicdesigninstitute.com/...  
Downloading http://www.humongousinsurance.com/...  
Downloading http://www.litwareinc.com/...  
Downloading http://www.lucernepublishing.com/...  
Downloading http://www.margiestravel.com/...  
Downloading http://www.northwindtraders.com/...  
Downloading http://www.proseware.com/...  
Downloading http://www.fineartschool.net...  
Downloading http://www.tailspintoys.com/...  
Downloaded 1801040 bytes in 3276 ms.  
```  
  
 因為其他工作執行其他工作在等候潛在的作業完成時，啟用過度訂閱時，可以更快速執行範例。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`download-oversubscription.cpp`然後執行的下列其中一個命令在 Visual Studio 命令提示字元視窗中。  
  
 **cl.exe /EHsc /MD /D"_AFXDLL"download-oversubscription.cpp**  
  
 **cl.exe /EHsc /MT download-oversubscription.cpp**  
  
## <a name="robust-programming"></a>穩固程式設計  
 之後您不再需要，一律停用過度訂閱。 請考慮不會處理另一個函式所擲回例外狀況的函式。 如果函式傳回前不停用過度訂閱，任何額外的平行工作也會過度訂閱目前內容。  
  
 您可以使用*資源擷取即初始化*(RAII) 模式，限制在指定範圍內的過度訂閱。 下 RAII 模式，是在堆疊上配置的資料結構。 該資料結構初始化或建立和終結或終結的資料結構時，釋放該資源時，取得資源。 RAII 模式可確保解構函式稱為封入範圍結束之前。 因此，資源正確管理時擲回例外狀況，或函式包含多個`return`陳述式。  
  
 下列範例會定義名為結構`scoped_blocking_signal`。 建構函式`scoped_blocking_signal`結構啟用過度訂閱和解構函式停用過度訂閱。  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 下列範例會修改主體`download`函式傳回前，已停用要用來確保過度訂閱的 RAII 方法。 這項技術可確保`download`方法是例外狀況安全。  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [內容](../../parallel/concrt/contexts.md)   
 [Context:: oversubscribe 方法](reference/context-class.md#oversubscribe)


